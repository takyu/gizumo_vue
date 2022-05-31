<template>
  <div>
    <h1 v-html="message" :class="classObject"></h1>
    <button @click="changeTextSize">large</button>
    <hr />
    <article v-for="post in posts" :key="post.title">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </article>
    <hr />
    <!-- v-show -> v-if ( Vueインスタンスを破棄するため ) -->
    <child-component v-if="isShow">
      <template #head>
        <p>head slot</p>
      </template>
      <template #default>
        <p>main slot</p>
        <p>main slot2</p>
      </template>
      <template #foot>
        <p>foot slot</p>
      </template>
    </child-component>
    <button @click="toggleShow">toggle isShow</button>
  </div>
</template>

<script>
  import ChildComponent from 'Components/ChildComponent';
  import axios from 'axios';

  export default {
    beforeCreate() {
      console.log('-----  beforeCreate  -----');
      console.log(this.message);
    },
    created() {
      console.log('-----  created  -----');
      console.log(this.posts);
      axios.get('/data.json').then((res) => {
        this.posts = res.data.posts;
      });
    },
    beforeMount() {
      console.log('----  beforeMount  -----');
      console.log(this.$el);
    },
    mounted() {
      console.log('-----  mounted  -----');
      console.log(this.$el);
    },
    beforeUpdate() {
      console.log('-----  beforeUpdate  -----');
    },
    updated() {
      console.log('-----  updated  -----');
    },
    beforeDestroy() {},
    data() {
      return {
        message: '-- lifecycle --',
        classObject: {
          'is-large': false,
        },
        posts: [],
        isShow: true,
      };
    },
    methods: {
      changeTextSize() {
        this.classObject = { ...this.classObject, 'is-large': true };
      },
      toggleShow() {
        this.isShow = !this.isShow;
      },
    },
    computed: {},
    components: {
      ChildComponent,
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
