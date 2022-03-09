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
};
</script>
