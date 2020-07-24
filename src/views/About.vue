<template>
  <div>
    <button @click="change1">改变对象属性触发</button>
    <button @click="change2">改变对象触发</button>
    <button @click="change3">改变对象深度触发</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from "vue-property-decorator";
interface Person {
  handler: string;
}
@Component
export default class Chart extends Vue {
  private personData: Person = {
    handler: "onPersonChanged2"
  };

  private personDatatwo: Person = {
    handler: "onPersonChanged2"
  };

  //绑定对象中的某个属性，只有当该属性发生变化时，触发该动作
  @Watch("personData.handler", { immediate: false, deep: false })
  onPersonChanged1(newVal: Person, oldVal: Person) {
    //这两个参数，分别是改变前后改变后的值
    console.log("newVal:", newVal);
    console.log("oldVal:", oldVal);
  }
  //绑定对象，只有当该对象发生变化时，触发该动作
  //@Watch("personData")这么写一样
  @Watch("personData", { immediate: false, deep: false })
  onPersonChanged2(newVal: Person, oldVal: Person) {
    console.log("newVal:", newVal);
    console.log("oldVal:", oldVal);
  }
  //但是上述两种过于麻烦，所以有了immediate和deep，默认值为false,代表立即实行和深度监听
  //immediate为true的时候，会刚开始时就执行一次，比如第一次渲染该页面
  //deep为true时，代表同时监听对象内部属性情况，内部变化，也会触发该函数
  @Watch("personDatatwo", { immediate: true, deep: true })
  onPersonChanged3(newVal: Person, oldVal: Person) {
    console.log("newVal:", newVal);
    console.log("oldVal:", oldVal);
  }

  change1() {
    this.personData.handler = "shitingbao";
  }

  change2() {
    this.personData = {
      handler: "shitingbao"
    };
  }

  change3() {
    this.personDatatwo.handler = "this change data";
  }
}
</script>
