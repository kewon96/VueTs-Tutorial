<template>
  <div id="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from 'vue'
import JobList from './components/JobList.vue';
import Job from './types/Job';
import OrderTerm from './types/OrderTerm';

export default defineComponent({
  name: 'App',
  components: {
    JobList
  },
  setup() {
    const jobs = ref<Job>([
      {
        title: 'farm worker',
        location: '김제시',
        salary: 300000,
        id: '1'
      },
      {
        title: 'fisher',
        location: '통영시',
        salary: 500000,
        id: '2'
      },
      {
        title: 'office',
        location: '서울시',
        salary: 400000,
        id: '3'
      },
      {
        title: 'police',
        location: '고양시',
        salary: 350000,
        id: '4'
      },
      {
        title: 'fireman',
        location: '성남시',
        salary: 800000,
        id: '5'
      },
      {
        title: 'professor',
        location: '서울시',
        salary: 250000,
        id: '6'
      }
    ])

    const order = ref<OrderTerm>('title');

    return { jobs, order }
  },
  methods: {
    handleClick(term: OrderTerm) {
      this.order = term;
    }
  }
})
</script>

<style lang="sass">
  header
    text-align: center

    .order
      margin-top: 20px

  button
    margin: 0 10px
    color: #1195c9
    border: 3px solid #1195c9
    background: #d5f0ff
    padding: 8px 16px
    border-radius: 4px
    cursor: pointer
    font-weight: bold

</style>
