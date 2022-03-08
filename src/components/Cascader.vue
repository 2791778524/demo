<template>
  <a-cascader
    :options="options"
    placeholder="请选择城市"
    @change="onChange"
    v-model="demo"
  />
</template>
<script>
export default {
  data() {
    return {
      options: [
        {
          value: "jiangsu",
          label: "江苏",
          children: [
            { id: '1',
              value: "nanjing",
              label: "南京",
            },
          ],
        },
      ],
      demo: ['jiangsu','nanjing']
    };
  },
  methods: {
    onChange(value) {
      if(value[1] === 'nanjing')
      {
          console.log('是');
      } else {
          console.log('否');
      }
    },
  },
};
</script>
