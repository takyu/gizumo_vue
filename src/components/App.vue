<template>
  <div>
    <!-- <h1>{{ message }}</h1> -->
    <!-- <h1 v-html="message" v-bind:class="{ 'is-green': isGreen }"></h1> -->
    <!-- <h1 v-html="message" v-bind:class="classObject"></h1> -->
    <h1 v-html="message" :class="classObject"></h1>
    <hr />
    <child-component v-show="isShow"></child-component>
    <hr />
    <!-- <p v-if="id === 1">1</p>
    <p v-else-if="id === 2">2</p>
    <p v-else>other</p> -->
    <template v-if="id === 1">
      <p>1-1</p>
      <p>1-2</p>
      <p>1-3</p>
    </template>
    <template v-else-if="id === 2">
      <p>2-1</p>
      <p>2-2</p>
      <p>2-3</p>
    </template>
    <hr />
    <template v-for="item in items">
      <li :key="item.id">{{ item.id }} - {{ item.title }}</li>
    </template>
    <hr />
    <template v-for="item in items">
      <child-component :key="item.id"></child-component>
    </template>
    <hr />
    <!-- <button v-on:click="count++">Add to Count</button> -->
    <button @click="count++">Add to Count</button>
    <p>{{ count }}回クリックしました。</p>
  </div>
</template>

<script>
import ChildComponent from 'Components/ChildComponent';
export default {
  //es6のメソッド記法
  data() {
    return {
      message: 'Hello Vue',
      isGreen: true,
      id: 2,
      classObject: {
        'is-green': true,
      },
      isShow: true,
      items: [
        {
          id: this.$uuid.v4(),
          title: '1番目のリスト',
        },
        {
          id: this.$uuid.v4(),
          title: '2番目のリスト',
        },
        {
          id: this.$uuid.v4(),
          title: '3番目のリスト',
        },
      ],
      count: 0,
    };
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
</style>
