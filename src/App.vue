<template>
  <div id="app">
    <p>{{ name }} - {{ age }}</p>
    <input type="text" v-model="newName">
    <button @click="changeName()">change name</button>
    <button @click="calcAge('+')">+</button>
    <button @click="calcAge('-')">-</button>
  </div>
</template>

<script lang="ts">
import {defineComponent, reactive, ref, toRefs} from 'vue'
import Job from './types/Job';

export default defineComponent({
  name: 'App',
  components: {},
  setup() {
    // const state = reactive({
    //   name: 'Link',
    //   newName: '',
    //   age: 26 as number | string
    // });
    //
    // return { ...toRefs(state)}

    const name = ref('Link');
    const age = ref<number | string>(26);
    const newName = ref('');

    return { name, age, newName }

  },
  methods: {
    changeName() {
      if(this.newName.blink())

      this.name = this.newName;

      this.newName = '';
    },
    calcAge(oper: string) {
      const vm = this;
      let age = vm.age;

      if(typeof age === 'string') {
        age = Number(age);
      }

      switch (oper) {
        case '+': age += 1; break;
        case '-': age -= 1; break;
      }

      vm.age = age;
    },
  }
})
</script>

<style lang="sass">


</style>
