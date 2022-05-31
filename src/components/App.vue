<template>
  <div>
    <h1 v-html="message" :class="classObject"></h1>
    <button @click="changeTextSize">large</button>
    <hr />
    <counter :count="count" @increment="incrementCount"></counter>
    <hr />
    <span>名前：</span>
    <input-text v-model="form.name"></input-text>
    <p>名前： {{ getInputName }}</p>
  </div>
</template>

<script>
  import ChildComponent from 'Components/ChildComponent';
  import Counter from 'Components/Counter';
  import InputText from 'Components/InputText';

  export default {
    data() {
      return {
        message: '-- emit --',
        classObject: {
          'is-large': false,
        },
        inputText: '',
        count: 0,
        form: {
          name: '',
        },
      };
    },
    methods: {
      changeTextSize() {
        this.classObject = { ...this.classObject, 'is-large': true };
      },
      incrementCount() {
        this.count++;
      },
    },
    computed: {
      getInputName() {
        return this.form.name;
      },
    },
    components: {
      ChildComponent,
      Counter,
      InputText,
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
