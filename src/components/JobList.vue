<template>
  <div class="job-list">
    <p>Ordered by {{ order }}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} won</p>
        </div>
        <div class="discription">
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Architecto, autem culpa enim eos error ex exercitationem fuga libero, magni provident quae sapiente tempora temporibus ut vel? Consectetur, debitis dicta dolor illum maiores minus quisquam sed vero voluptate voluptatum. A accusantium amet at dicta enim fugit illum magni similique unde velit!</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import {computed, defineComponent, PropType} from 'vue'
import Job from '../types/job';
import OrderTerm from "../types/OrderTerm";

/**
 * Vue.Ts Annotating Props
 * https://v3.vuejs.org/guide/typescript-support.html#annotating-props
 *
 * Props Validation
 * https://vuejs.org/v2/guide/components-props.html#Prop-Validation
 */
export default defineComponent ({
  props: { // props Validation
    jobs: {
      required: true, // 필수
      type: Array as PropType<Job[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>
    }
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((x1: Job, x2: Job) => {
        return x1[props.order] > x2[props.order] ? 1 : -1;
      });
    })

    return { orderedJobs };
  }
})
</script>

<style lang="sass" scoped>
  .job-list
    max-width: 960px
    margin: 40px auto

    ul
      padding: 0

    li
      list-style-type: none
      background: white
      padding: 16px
      margin: 16px 0
      border-radius: 4px

    h2
      margin: 0 0 10px
      text-transform: capitalize

  .salary
    display: flex

    img
      width: 30px

    p
      color: #17bf66
      font-weight: bold
      margin: 10px 4px

</style>