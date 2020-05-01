<!--
 * @Author: your name
 * @Date: 2020-03-28 02:33:37
 * @LastEditTime: 2020-03-29 12:49:59
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \xuwentest\src\components\common\layout.vue
 -->
<template>
  <div class="layout" @mouseenter="getmodules" >
      <component :is="item" v-for="(item,key) in html" :key="key"></component> 
  </div>
</template>

<script>
import * as modlueobj from "../modules";
export default {
    components:modlueobj.default,
  data() {
      console.log(modlueobj.default)
    return {
        html:[]
    };
  },
  methods: {
      getmodules(e){
          const arr=Object.keys(modlueobj.default)
          if(e.fromElement){
              const text=e.fromElement.innerText
              if(text&&arr.indexOf(text)!=-1){
                  this.html.push(e.fromElement.innerText)
              }
          }
          
          
          console.log(e.fromElement);
          
          console.log(arr)
        //   arr.
      }
  }
};
</script>

<style lang="scss" scoped>
.layout {
  width: 1200px;
  margin: 0 auto;
  min-height: 500px;
  background-color: tan;
}
</style>