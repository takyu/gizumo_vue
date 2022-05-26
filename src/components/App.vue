<template>
  <div>
    <h1>-- methods --</h1>
    <hr />
    <button @click="incrementCount">Add to count</button>
    <p>{{ count }}回クリックされました</p>
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
  methods: {
    incrementCount() {
      this.count++;
    },
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
