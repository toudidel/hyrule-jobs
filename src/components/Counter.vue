<template>
  <div>
    <button @click="increment">Increment</button>
    <div>{{ count }}</div>
    <button @click="decrement">Decrement</button>
  </div>
</template>

<script lang="ts">
import {Vue} from "vue-class-component";

export default class Counter extends Vue {
  count = 0;

  public increment(): void {
    this.count++;
  }

  public decrement(): void {
    this.count--;
  }
}
</script>

<style scoped>

</style>
