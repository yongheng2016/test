<template>
 <div class="child-1">
 <p>in child1:</p>
 <p>props: {{pChild1}}</p>
 <p>$attrs: {{$attrs}}</p>
 <hr>
 <child2 v-bind="$attrs" v-on="$listeners"></child2>
    <!-- B组件在中间起到了承上启下的作用（链接 A | C 组件） -->
    <!-- A组件中能直接监听C组件提交的事件的原因在于 B组件调用C组件时 使用 v-on 绑定了$listeners 属性 -->
    <!-- 通过v-bind 绑定$attrs属性，C组件可以直接获取到A组件中传递下来的props（除了B组件中props声明的） -->
 </div>
</template>
<script>
import Child2 from "./TestC.vue";
export default {
  props: ["pChild1"],
  data() {
    return {};
  },
  inheritAttrs: false,    // --> 默认true,false情况下可以去除限制 
  components: { Child2 },
  mounted() {
    this.$emit("test1");
  }
};
</script>
