<template>
  <div>算法</div>
</template>

<script>
export default {
  mounted() {
    let newArr = this.shellSort([
      34, 1, 56, 3435, 12, 56, 23, 56, 12, 57,
    ]);
    console.log(newArr);
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
    shellSort(arr) {
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
  },
};
</script>

<style>
</style>