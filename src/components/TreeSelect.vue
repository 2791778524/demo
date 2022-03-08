<template>
  <div class="container">
    <div class="tree_select" style="width: 20%; margin: auto">
      <a-tree-select
        style="width: 100%"
        :tree-data="treeData"
        tree-checkable
        :show-checked-strategy="SHOW_PARENT"
        search-placeholder="Please select"
        placeholder="请选择参数"
        searchPlaceholder="111"
      />
    </div>
    <div class="badge">
      <a-badge count="5">
        <a href="#" class="head-example" />
      </a-badge>
      <a-badge count="0" show-zero>
        <a href="#" class="head-example" />
      </a-badge>
      <a-badge>
        <a-icon slot="count" type="clock-circle" style="color: #f5222d" />
        <a href="#" class="head-example" />
      </a-badge>
    </div>
    <div
      :style="{
        width: '300px',
        border: '1px solid #d9d9d9',
        borderRadius: '4px',
      }"
    >
      <a-calendar :fullscreen="false" @panelChange="onPanelChange" />
    </div>
  </div>
</template>

<script>
import { TreeSelect } from "ant-design-vue";
const SHOW_PARENT = TreeSelect.SHOW_PARENT;

const treeData = [
  {
    title: "Node1",
    value: "0-0",
    key: "0-0",
    children: [
      {
        title: "Child Node1",
        value: "0-0-0",
        key: "0-0-0",
      },
    ],
  },
  {
    title: "Node2",
    value: "0-1",
    key: "0-1",
    children: [
      {
        title: "Child Node3",
        value: "0-1-0",
        key: "0-1-0",
        disabled: true,
      },
      {
        title: "Child Node4",
        value: "0-1-1",
        key: "0-1-1",
      },
      {
        title: "Child Node5",
        value: "0-1-2",
        key: "0-1-2",
      },
    ],
  },
];
export default {
  data() {
    return {
      //   value: ["0-0-0"],
      treeData,
      SHOW_PARENT,
    };
  },
  methods: {
    onPanelChange(value, mode) {
      console.log(value, mode);
    },
  },
};
</script>
<style scoped>
.badge {
  display: flex;
  justify-content: space-around;
  padding: 20px;
}
</style>
