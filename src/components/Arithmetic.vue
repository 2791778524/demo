<template>
  <div>算法</div>
</template>

<script>
export default {
  mounted() {
    let newArr = this.shellSortDown([34, 1, 56, 3435, 12, 56, 23, 56, 12, 57]);
    // console.log(newArr);
    let maxProfit = this.getMacProfit([
      34, 1, 56, 3435, 12, 56, 23, 56, 12, 57,
    ]);
    // console.log(maxProfit);

    // console.log(this.getFactorial(2,2));

    // console.log(this.getArrayDuplicate([1,2,1,5,6,3,5,3,1,2,6,8,76,9]));
    // this.getTimer();
    // console.log(this.getFibonacci(10));
    console.log(this.binary_search([1, 2, 3, 4, 5, 6, 7, 8, 9], 4));
  },
  methods: {
    //冒泡排序降序
    bubbleSortdown(arr) {
      for (let i = 0; i < arr.length - 1; i++) {
        for (let j = 0; j < arr.length - 1; j++) {
          if (arr[j] < arr[j + 1]) {
            let temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
          }
        }
      }
      return arr;
    },
    //冒泡排序升序
    bubbleSortUp(arr) {
      for (let i = 0; i < arr.length - 1; i++) {
        for (let j = 0; j < arr.length - 1; j++) {
          if (arr[j] > arr[j + 1]) {
            let temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
          }
        }
      }
      return arr;
    },
    //选择排序升序
    selectionSortUp(arr) {
      let minIndex, temp;
      for (let i = 0; i < arr.length - 1; i++) {
        minIndex = i;
        for (let j = i + 1; j < arr.length; j++) {
          if (arr[j] < arr[minIndex]) {
            minIndex = j;
          }
        }
        temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
      }
      return arr;
    },
    //选择排序法降序
    selectSortDown(arr) {
      for (let i = 0; i < arr.length - 1; i++) {
        let maxIndex = i;
        for (let j = i + 1; j < arr.length; j++) {
          if (arr[j] > arr[maxIndex]) {
            maxIndex = j;
          }
        }
        let temp = arr[i];
        arr[i] = arr[maxIndex];
        arr[maxIndex] = temp;
      }
      return arr;
    },
    //插入排序法升序
    insertionSortUp(arr) {
      var len = arr.length;
      var preIndex, current;
      for (var i = 1; i < len; i++) {
        preIndex = i - 1;
        current = arr[i];
        while (preIndex >= 0 && arr[preIndex] > current) {
          arr[preIndex + 1] = arr[preIndex];
          preIndex--;
        }
        arr[preIndex + 1] = current;
      }
      return arr;
    },
    //插入排序法降序
    insertionSortDown(arr) {
      for (let i = 1; i < arr.length; i++) {
        let index = i - 1;
        let current = arr[i];
        while (index >= 0 && arr[index] < current) {
          arr[index + 1] = arr[index];
          index--;
        }
        arr[index + 1] = current;
      }
      return arr;
    },
    //希尔排序升序
    shellSortUp(arr) {
      var len = arr.length,
        temp,
        gap = 1;
      while (gap < len / 3) {
        //动态定义间隔序列
        gap = gap * 3 + 1;
      }
      for (gap; gap > 0; gap = Math.floor(gap / 3)) {
        for (var i = gap; i < len; i++) {
          temp = arr[i];
          for (var j = i - gap; j >= 0 && arr[j] > temp; j -= gap) {
            arr[j + gap] = arr[j];
          }
          arr[j + gap] = temp;
        }
      }
      return arr;
    },
    //希尔排序降序
    shellSortDown(arr) {
      var len = arr.length,
        temp,
        gap = 1;
      while (gap < len / 3) {
        //动态定义间隔序列
        gap = gap * 3 + 1;
      }
      for (gap; gap > 0; gap = Math.floor(gap / 3)) {
        for (var i = gap; i < len; i++) {
          temp = arr[i];
          for (var j = i - gap; j >= 0 && arr[j] < temp; j -= gap) {
            arr[j + gap] = arr[j];
          }
          arr[j + gap] = temp;
        }
      }
      return arr;
    },
    //获取数组中的最大插值
    getMacProfit(arr) {
      let max = arr[0],
        min = arr[0];
      for (let i = 0; i < arr.length; i++) {
        if (max < arr[i]) {
          max = arr[i];
        }
        if (min > arr[i]) {
          min = arr[i];
        }
      }
      return max - min;
    },
    //获取一个数的阶乘
    getFactorial(num, n) {
      let result = 1;
      for (let i = 0; i < n; i++) {
        result = result * num;
      }
      return result;
    },
    //数组去重
    getArrayDuplicate(arr) {
      for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
          if (arr[i] === arr[j]) {
            arr.splice(j, 1);
            j--;
          }
        }
      }
      return arr;
    },
    //获取当前的时间
    getTimer() {
      let timer = null;
      setInterval(() => {
        let time = new Date();
        let y = time.getFullYear();
        let m = time.getMonth() + 1;
        let d = time.getDate();
        let h = time.getHours();
        let min = time.getMinutes();
        let s = time.getSeconds();
        if (m < 10) {
          m = `0${m}`;
        }
        if (h < 10) {
          h = `0${h}`;
        }
        if (min < 10) {
          min = `0${min}`;
        }
        if (s < 10) {
          s = `0${s}`;
        }
        return `${y}年${m}月${d}日： ${h}:${min}:${s}`;
      }, 1000);
    },
    //生成斐波那契数列
    getFibonacci(n) {
      let resArray = [0, 1];
      let f1 = 0;
      let f2 = 1;
      let i = 2;
      while (i < n) {
        resArray.push(resArray[i - 1] + resArray[i - 2]);
        i++;
      }
      return resArray;
    },
    //二分查找
    binary_search(arr, key) {
      let low = 0;
      let high = arr.length - 1;
      while (low <= high) {
        let mid = parseInt((low + high) / 2);
        if (key === arr[mid]) {
          return mid;
        } else if (key < arr[mid]) {
          high = mid - 1;
        } else if (key > arr[mid]) {
          low = mid + 1;
        }
      }
      return -1;
    },
  },
};
</script>

<style>
</style>