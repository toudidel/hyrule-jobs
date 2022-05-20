<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo" style="width:75px">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import JobList from "@/components/JobList.vue";
import OrderTerm from "@/types/OrderTerm";
import Job from "@/types/Job";

@Options({
  components: {
    JobList
  }
})
export default class App extends Vue {

  order: OrderTerm = 'title';
  jobs: Job[] = [
    { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
    { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
    { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
    { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
    { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
  ];

  handleClick = (term: OrderTerm) => {
    this.order = term
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
