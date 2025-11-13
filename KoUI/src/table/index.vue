<!--
 * @Author: zhangke
 * @Date: 2025-11-13 15:48:54
 * @LastEditors: zhangke
 * @LastEditTime: 2025-11-13 17:31:20
 * @Description: 
-->

<template>
  <div class="ko-table">
    {{ str }}
    <div class="ko-table__header-wrapper">
      <table>
        <thead>
          <th>
            <div class="cell">姓名</div>
          </th>
          <th>
            <div class="cell">邮箱</div>
          </th>
        </thead>
      </table>
    </div>

    <div class="ko-table__body-wrapper">
      <table>
        <tbody>
          <tr class="ko-table__row">
            <td>
              <div class="cell">张三</div>
            </td>
            <td>
              <div class="cell">
                <a href="mailto:<EMAIL>">sadas</a>
              </div>
            </td>
          </tr>
          <tr class="ko-table__row">
            <td>
              <div class="cell">张三</div>
            </td>
          </tr>
          <tr class="ko-table__row">
            <td>
              <div class="cell">张三</div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="ko-table__footer-wrapper">
      <table class="ko-table__footer">
        <tfoot>
          <tr class="ko-table__row">
            <td>
              <div class="cell">合计</div>
            </td>
          </tr>
        </tfoot>
      </table>
    </div>
  </div>
</template>
<script setup lang="ts">
  const str = "stringstrings";
  defineOptions({
    name: "ko-table",
  });
</script>
<style scoped></style>
