<template>
  <div class="home">
    <HelloWorld msg="Welcome" :array="array" />
    <video width="320" height="240" controls v-if="false">
      <source src="../../public/video/fire.mp4" type="video/mp4" />
    </video>
    <P>{{this.list[0].number}}</p>
    <button @click="getChange">点击</button>
  </div>
</template>

<script lang="ts">
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import { Component, Prop, Vue, Watch } from "vue-property-decorator";

@Component({
  components: {
    HelloWorld
  }
})
export default class Home extends Vue {
  private array: Array<any> = [1, 2, 3, 4];
  private list: Array<any> = [{name:"p1p1",number:123},{name:"hahaa",number:7845}];
  private a: any = 23;
  public set = new Map();
  private length: string = this.$store.state.aa

  getChange(mag: any) {
   this.$store.state.aa +=1
    // this.array[1] += 1;
    // this.$set(this.array, 0, 4);
    // console.log("26行array:" + this.array);
  }
 
  get lengthchange(){
      return this.$store.state.aa
    }
  @Watch("lengthchange", { immediate: true, deep: true })
  numberchange(newVal: any, oldVal: any) {
    this.$set(
      this.list[0],
      "number",
      newVal
    )
    console.log(newVal)
  }
  created() {
    const hah = this.set.set(1, this.array);
    // this.$set(this.array, 1, 10);
    // hah.forEach((key, val) => console.log(key + ": " + val));
    // console.log("array:" + this.array);
    // console.log("hah的长度：" + hah.size);
    // console.log("hah的value：" + Array.from(hah));
  }
}
</script>
