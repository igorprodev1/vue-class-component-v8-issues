<template>
  <div></div>
</template>

<script lang="ts">
import { Options, Vue, mixins } from "vue-class-component";

class M1 extends Vue {
  get m1Computed() {
    return "m1computed call";
  }
}

class M11 extends mixins(M1) {
  get m11Computed() {
    return "m11computed call";
  }
}

class M2 extends mixins(M11) {
  get m2Computed() {
    return "m2computed call";
  }
}

export default class App extends mixins(M2) {
  get appComputed() {
    return "app computed";
  }

  mounted() {
    console.log((this as any).m1Computed);
    console.log((this as any).m11Computed);
    console.log((this as any).m2Computed);
    console.log((this as any).appComputed);
    console.log(this);
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
