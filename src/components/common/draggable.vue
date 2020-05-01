<!--
 * @Author: your name
 * @Date: 2020-03-28 01:41:08
 * @LastEditTime: 2020-03-28 16:37:33
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \xuwentest\src\components\common\draggable.vue
 -->
<template>
  <div>
    <div
      draggable
      :class="element.drag?'draggableitem sortable-chosen':'draggableitem'"
      @dragstart="isChosed(element.v)"
      @dragend="isNotChosed(element.v)"
      v-for="element in myArray"
      :key="element.v"
    >{{element.v}}</div>
  </div>
</template>

<script>
import * as moduleobj from "../modules";
const arr = [];
Object.keys(moduleobj.default).forEach(v => {
  arr.push({ v, drag: false });
});
export default {
  data() {
    return {
      myArray: arr
    };
  },
  components: {},
  methods: {
    isChosed(e) {
      this.myArray.map(v => {
        if (v.v == e) {
          v.drag = true;
        }
      });
      console.log(this.myArray);
    },
    isNotChosed(e) {
      this.myArray.map(v => {
        if (v.v == e) {
          v.drag = false;
        }
      });
      console.log(this.myArray);
    }
  }
};
</script>

<style lang="scss" >
.draggableitem {
  background-color: steelblue;
  float: left;
  width: 80px;
  height: 80px;
  line-height: 80px;
  margin-left: 13px;
  margin-top: 10px;
}
.sortable-chosen {
  background-color: skyblue;
}
</style>