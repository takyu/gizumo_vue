<template>
  <div>
    <h1 v-html="message" :class="classObject"></h1>
    <button @click="changeTextSize">large</button>
    <hr />
    <counter></counter>
    <hr />
    <!-- <p>{{ $store.state.count }}回クリックされました</p> -->
    <!-- <hr /> -->
  </div>
</template>

<script>
  import ChildComponent from 'Components/ChildComponent';
  import axios from 'axios';
  import Counter from './Counter.vue';

  export default {
    data() {
      return {
        message: '-- lifecycle --',
        classObject: {
          'is-large': false,
        },
      };
    },
    methods: {
      changeTextSize() {
        this.classObject = { ...this.classObject, 'is-large': true };
      },
    },
    computed: {},
    components: {
      ChildComponent,
      Counter,
    },
  };
</script>

<style scoped>
  hr {
    margin: 16px 0;
  }

  .is-green {
    color: green;
  }

  .is-large {
    font-size: 60px;
  }
</style>
