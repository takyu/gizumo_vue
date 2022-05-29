<template>
  <div>
    <h1 v-html="message" :class="classObject"></h1>
    <button @click="changeTextSize">large</button>
    <hr />
    <input type="text" v-model="inputText" />
    <p>computed: {{ getUpperCaseText }}</p>
    <p>methods: {{ showUpperCaseText() }}</p>
    <hr />
    <button @click="addDescription">add description</button>
    <p>{{ leads.description }}</p>
  </div>
</template>

<script>
  import ChildComponent from 'Components/ChildComponent';
  export default {
    //es6のメソッド記法
    data() {
      return {
        message: '-- data --',
        classObject: {
          'is-large': false,
        },
        inputText: '',
        leads: {
          message: '<span>Hello Vue</span>',
          description: '',
        },
      };
    },
    methods: {
      showUpperCaseText() {
        return this.inputText.toUpperCase();
      },
      changeTextSize() {
        this.classObject = { ...this.classObject, 'is-large': true };
      },
      addDescription() {
        this.leads.description = 'Vue-lesson';
      },
    },
    computed: {
      getUpperCaseText() {
        return this.inputText.toUpperCase();
      },
    },
    watch: {
      inputText: (value, oldValue) => {
        console.log(`value -> ${value}`);
        console.log(`oldValue -> ${oldValue}`);
      },
      leads: {
        handler() {
          console.log('add description');
        },
        deep: true,
      },
      // leads.descriptionの変更のみを監視したい場合
      // 'leads.description': {
      //   handler() {
      //     console.log('add description');
      //   },
      //   deep: true,
      // },
    },
    components: {
      ChildComponent,
    },
  };
</script>

<style scoped>
  /* h1 {
  color: green;
} */

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
