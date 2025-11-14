<!--
 * @Author: zhangke
 * @Date: 2025-11-13 15:48:54
 * @LastEditors: zhangke
 * @LastEditTime: 2025-11-14 17:38:11
 * @Description: 表格组件
-->

<template>
  <div class="ko-table">
    <div class="ko-table-wrapper" :style="ObjectToStyleFormat(tableStyle)">
      <!-- 表头 -->
      <div class="ko-table__header-wrapper">
        <table class="ko-table__header">
          <colgroup>
            <col
              v-for="(item, index) in headerColgroup"
              :key="index"
              :name="item.name"
              :width="item.width"
            />
          </colgroup>
          <thead>
            <tr>
              <th
                v-for="(item, index) in headerTableDate"
                :key="index"
                :colspan="item.colspan"
                :rowspan="item.rowspan"
              >
                <component :is="item.cellContent" />
              </th>
            </tr>
          </thead>
        </table>
      </div>
      <!-- 表体 -->
      <div class="ko-table__body-wrapper">
        <table class="ko-table__body">
          <tbody>
            <tr class="ko-table__row">
              <td>
                <div class="cell">张三</div>
              </td>
              <td></td>
            </tr>
          </tbody>
        </table>
      </div>
      <!-- 表脚 -->
      <div class="ko-table__footer-wrapper">
        <table class="ko-table__footer">
          <tfoot>
            <tr class="ko-table__row">
              <td>
                <div class="cell">合计</div>
                <font color="red">4</font>
              </td>
            </tr>
          </tfoot>
        </table>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
  import { ref, h, type VNode } from "vue";

  const tableStyle = ref({
    width: "0px",
  });

  /** 表头表格 列组 */
  const headerColgroup = ref<
    Array<{
      name: string;
      width: string;
    }>
  >([]);

  const headerTableDate = ref<
    Array<{
      className: string;
      colspan: number;
      rowspan: number;
      cellContent: VNode;
    }>
  >([]);

  const setAllConfig = () => {
    const columnNumber = 20;

    for (let i = 0; i < columnNumber; i++) {
      const columnName = `ko-table_1_column_${i + 1}`;
      const columnWidth = `200px`;
      headerColgroup.value.push({
        width: columnWidth,
        name: columnName,
      });

      headerTableDate.value.push({
        className: columnName,
        colspan: 1,
        rowspan: 1,
        cellContent: h(
          "div",
          {
            class: "cell",
          },
          `第${i + 1}列`
        ),
      });
    }

    calculateTableWidth();
  };

  const calculateTableWidth = () => {
    headerColgroup.value.forEach(item => {
      tableStyle.value.width += item.width;
      tableStyle.value.width =
        parseInt(tableStyle.value.width || "0") + parseInt(item.width) + "px";
    });
  };

  setAllConfig();

  interface StyleObject {
    [key: string]: string | number;
  }

  const ObjectToStyleFormat = (obj: StyleObject) => {
    let style = "";
    for (const key in obj) {
      style += `${key}:${obj[key]};`;
    }
    return style;
  };

  defineOptions({
    name: "ko-table",
  });
</script>
<style scoped>
  table {
    width: auto; /* 取消100%宽度，让列宽决定表格总宽 */
    /* 或明确设置表格宽度，确保列宽总和不超过 */
    /* width: 800px; */
  }
  td,
  th {
    max-width: inherit; /* 继承col设置的宽度 */
    white-space: nowrap; /* 禁止文本换行（可选） */
    overflow: hidden; /* 超出部分隐藏（可选） */
  }

  .ko-table {
    width: 100%;
    overflow: auto;
  }
  .ko-table-wrapper {
  }

  .ko-table__header-wrapper {
    width: 100%;
    overflow: auto;
  }
</style>
