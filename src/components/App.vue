<template>
  <div>
    <h1 v-html="message" :class="classObject"></h1>
    <p>{{ description }}</p>
    <button @click="addDescription">add description</button>
    <hr />
    <template v-for="category in categories">
      <p :key="category">
        {{ category }}
      </p>
    </template>
    <hr />
    <button @click="updateText">update text</button>
    <hr />
    <button @click="changeTextSize">large</button>
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
        description: '',
        items: [
          {
            id: this.$uuid.v4(),
            title: '1番目のリスト',
          },
          {
            id: this.$uuid.v4(),
            title: '２番目のリスト',
          },
          {
            id: this.$uuid.v4(),
            title: '3番目のリスト',
          },
        ],
        categories: ['Javascript', 'jQuery'],
      };
    },
    methods: {
      addDescription() {
        this.description = 'Vue-lesson';
        console.log(this);
        console.log(this.description);
      },
      updateText() {
        // this.categories.splice(1, 1, 'Vue.js');
        // this.$set(this.categories, 1, 'Vue.js');
        // this.categories.splice(2, 1, 'Vue.js');
        this.$set(this.categories, 2, 'Vue.js');
      },
      changeTextSize() {
        // this.classObject = Object.assign({}, this.classObject, {
        //   'is-large': true,
        // });
        // this.classObject = { ...this.classObject, 'is-large': true };
        this.$set(this.classObject, 'is-large', true);
      },
    },
    computed: {},
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
