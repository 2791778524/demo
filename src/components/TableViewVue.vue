<template>
  <a-table :columns="columns" :data-source="data" :pagination="false">
    <a slot="name" slot-scope="text">{{ text }}</a>
  </a-table>
</template>
<script>
const columns = [
  {
    title: 'Name',
    dataIndex: 'name',
    key: 'name',
    scopedSlots: { customRender: 'name' },
    align: 'left'
  },
  {
    title: 'Age',
    dataIndex: 'age',
    key: 'age',
    width: 80,
  },
  {
    title: 'Address',
    dataIndex: 'address',
    key: 'address 1',
    ellipsis: true,
  },
  {
    title: 'sex',
    dataIndex: 'sex',
    key: 'sex',
    ellipsis: true,
  },
  {
    title: 'tel',
    dataIndex: 'tel',
    key: 'tel',
    ellipsis: true,
  },
];

const data = [
  {
    key: '1',
    name: 'John Brown',
    age: 32,
    address: 'New York No. 1 Lake Park, New York No. 1 Lake Park',
    tel: '11111111111',
    sex: '男',
    tags: ['nice', 'developer'],
  },
  {
    key: '2',
    name: 'Jim Green',
    age: 42,
    address: 'London No. 2 Lake Park, London No. 2 Lake Park',
    tel: '222222222',
    sex: '女',
    tags: ['loser'],
  },
  {
    key: '3',
    name: 'Joe Black',
    age: 32,
    address: '1111',
    tags: ['cool', 'teacher'],
  },
];

export default {
  data() {
    return {
      data,
      columns,
    };
  },
};
</script>
