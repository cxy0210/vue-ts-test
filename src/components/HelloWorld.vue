<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{array.length}}</p>
    <button @click="changestore">修改</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  @Prop() readonly array!: Array<any>;
  changestore(){
    this.$store.state.aa +=1
  }
}
</script>
<style scoped>
</style>
