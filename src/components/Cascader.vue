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
    }
  },
  mounted() {
    let str = 'abc'
    let newStr = null
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


    let str1 = '  lll   a    '
    //消除字符串头部空格
    // console.log(str1.trimStart());
    //消除字符串尾部空格
    // console.log(str1.trimEnd());

    let str2 = 'abcabc'
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
    console.log(Math.sign(3)); //1
    console.log(Math.sign(-4));//-1
    console.log(Math.sign(0)); //0
    console.log(Math.sign(undefined));//NaN
  }
};
</script>
