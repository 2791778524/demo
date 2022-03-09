<template>
  <div>
    <a-cascader
      :options="options"
      placeholder="请选择城市"
      @change="onChange"
      v-model="demo"
    />
    <div style="width: 20%; margin: auto">
      <a-input prefix="￥" suffix="RMB" v-model="money" />
      <a-input-number
        id="inputNumber"
        v-model="value"
        :min="1"
        :max="10"
        @change="onChangeNumber"
      />
      <a-rate
        v-model="stars"
        :default-value="2.5"
        allow-half
        @change="change"
      />
    </div>
    <div>
      <a-switch default-checked @change="onChangeSwitch" />
    </div>
    <button>点击我</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: 1,
      money: 12000,
      stars: 3,
      options: [
        {
          value: "jiangsu",
          label: "江苏",
          children: [
            {
              id: "1",
              value: "nanjing",
              label: "南京",
              children: [
                {
                  value: "jiangningqu",
                  label: "江宁区",
                },
                {
                  value: "qinghuaiqu",
                  label: "秦淮区",
                },
                {
                  value: "gulouqu",
                  label: "鼓楼区",
                },
              ],
            },
          ],
        },
      ],
      demo: ["jiangsu", "nanjing", "jiangningqu"],
    };
  },
  methods: {
    onChange(value) {
      if (value[1] === "nanjing") {
        console.log("是");
      } else {
        console.log("否");
      }
    },
    onChangeNumber(value) {
      console.log(value);
    },
    change(value) {
      this.stars = value;
    },
    onChangeSwitch(value) {
      // console.log(value);
    },
    
    //防抖
    fangdou(fn) {
      let timer = null
      return function() {
        if(!isNaN(timer)) {
          timer = clearTimeout(timer)
        } else {
          timer = setTimeout(()=> {
            fn()
          },1000)
        }
      }
    },
  },

  mounted() {
    let str = "abc";
    let newStr = null;
    //返回一个新的字符串，将源字符串循环多少次
    // newStr = str.repeat(3)
    // console.log(newStr);

    //字符串补全功能
    //在字符串之前补全
    // newStr = str.padStart(8, 'a')
    // console.log(newStr);
    //在字符串之后补全
    // newStr = str.padEnd(8,'b')
    // console.log(newStr);

    let str1 = "  lll   a    ";
    //消除字符串头部空格
    // console.log(str1.trimStart());
    //消除字符串尾部空格
    // console.log(str1.trimEnd());

    let str2 = "abcabc";
    //字符串替换
    // console.log(str2.replace(/b/g,'d'))
    // console.log(str2.replaceAll('b','_'))

    //返回对应位置的字符
    // console.log(str2.at(3));

    //查看一个数是否有限
    // console.log(Number.isFinite(5));  //true
    // console.log(Number.isFinite(5.1));  //true
    // console.log(Number.isFinite(NaN));  //false
    // console.log(Number.isFinite('foo')); //false

    //判断是否为NaN
    // console.log(Number.isNaN(NaN));  //true

    //判断一个数值是否为整数
    // console.log(Number.isInteger(34.4)); //false
    // console.log(Number.isInteger(34));  //true

    //判断一个整数是否在最大范围内
    // console.log(Number.isSafeInteger(9007199254740990)) //true
    // console.log(Number.isSafeInteger(9007199254740992)) //false

    //去除一个数的小数部分
    // console.log(Math.trunc(34.55)); //34
    // console.log(Math.trunc(NaN)); //NaN

    // console.log(Math.trunc('foo'));//NaN

    //判断一个属是正数、负数还是零  正数 +1 负数 -1 零 0
    // console.log(Math.sign(3)); //1
    // console.log(Math.sign(-4));//-1
    // console.log(Math.sign(0)); //0
    // console.log(Math.sign(undefined));//NaN

    /* function add(...value) {
      console.log(...value);
    }
    add(1,2,3,4) */

    /* function push(array, ...items) {
      items.forEach((item)=>{
        array.push(item)
      })
      console.log(array);
    }

    push([],1,2,3,4,5,6,7,8,9) */

    //深拷贝
    function deepClone(obj) {
      let objClone = Array.isArray(obj) ? [] : {};
      if (obj && typeof obj === "object") {
        for (let key in obj) {
          if (obj[key] && typeof obj[key] === "object") {
            objClone[key] = deepClone(obj[key]);
          } else {
            objClone[key] = obj[key];
          }
        }
      }
      return objClone;
    }
    let arr2 = {
      name: "张三",
      age: 18,
      sex: "男",
      hobby: ['吃饭','睡觉','打豆豆'],
      obj: {
        tel: 10086,
        address: '北京紫禁城',
        nation: '汉'
      }
    }
    let newArray = deepClone(arr2)

    // newArray.obj.tel = 110
    // console.log(arr2);
    // console.log(newArray);


    let arr3 = JSON.parse(JSON.stringify(arr2))
    arr3.obj.nation = '傣族'
    /* console.log(arr2);
    console.log(arr3); */
    let str3 = 'asdfgh'
    
    //字符串反转
    // console.log(str3.split('').reverse().join(''));
    
    //返回字符首次出现的位置
    let str4 = 'stringt'
    // console.log(str4.indexOf('t'));
    
    //截取字符串
    // console.log(str4.substring(0,3));

    let test = [
      {
        name: '张三',
        age: 18,
        sex: '男',
        address: '南京市江宁区'
      },
      {
        name: '小红',
        age: 20,
        sex: '女',
        address: '南京市江宁区'
      },
      {
        name: '小明',
        age: 19,
        sex: '男',
        address: '南京市江宁区'
      }
    ]
    //过滤器
    let result = test.filter((item)=>{
      return item.sex === '女'
    })
    //每一项都符合条件时返回true否则返回false
    let result1 = test.every((item)=>{
      return item.address === '南京市江宁区'
    })
    //只要有一项符合返回true负责返回false
    let result2 = test.some((item) => {
      return item.sex === '女'
    })
    let result3 = test.map((item) => {
      if(item.name === '小明')
      {
        item.address = '上海市浦口区'
      }
      return item
    })
    //不可返回数据
    let result4 = []
    test.forEach((item)=>{
      if(item.sex === '男')
      {
        item.hobby = '打篮球'
      }
      result4.push(item)
    })
    console.log(result4);

    //返回符合条件的数组下标 无符合返回-1
    let index = test.findIndex((item) => item.sex === '女')

    //返回首次符合条件的数组元素
    let result5 = test.find((item)=>item.sex === '男')
    console.log(result5);

    //防抖
    let btnDom = document.documentElement.getElementsByTagName('button')[1]
    btnDom.addEventListener('click',this.fangdou(function(){console.log(111111);}))
    
  },
  
};
</script>
