<template>
  <div class="job-list">
    <p>Ordered by {{ order }}</p>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <div class="flr"><i>{{ job.location }}</i></div>
        <h2>{{ job.title }}</h2>
        <div class="salary">
          <img src="../assets/rupee.svg" alt="rupee icon">
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Rem omnis voluptatum eius doloremque optio iusto sequi dignissimos. Pariatur earum assumenda dolores possimus quidem quam, reprehenderit aliquid consequuntur amet non facere.</p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<script lang="ts">
import {Vue} from "vue-class-component";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";
import {Prop} from "vue-property-decorator";

export default class JobList extends Vue {

  @Prop() readonly jobs!: Job[];
  @Prop({ default: 'title' }) readonly order!: OrderTerm;

  get orderedJobs(): Job[] {
    return [...this.jobs].sort((a: Job, b: Job) => {
      return a[this.order] > b[this.order] ? 1 : -1
    })
  }
}
</script>

<style scoped>
  .flr {
    float: right;
  }
  .job-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .job-list ul {
    padding: 0
  }
  .job-list li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .job-list h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
  }
  .salary {
    display: flex;
  }
  .salary img {
    width: 30px;
  }
  .salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
  }
  .list-move {
    transition: all 1s;
  }
</style>
