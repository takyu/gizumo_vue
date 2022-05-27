<template>
  <div>
    <template v-for="item in items">
      <!-- Vue.js 3.x. -->
      <!-- https://eslint.vuejs.org/rules/no-v-for-template-key-on-child.html -->
      <!-- Vue.js 2.x -->
      <!-- https://eslint.vuejs.org/rules/no-v-for-template-key.html -->
      <!-- Vue 3.x では、:key は、template 側に、 -->
      <!-- Vue 2.x では、:key は、child-component 側に書く -->
      <child-component :title="item.title" :key="item.id">
        <span>slot content</span>
      </child-component>
    </template>
  </div>
</template>

<script>
import ChildComponent from 'Components/ChildComponent';
export default {
  //es6のメソッド記法
  data() {
    return {
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
    };
  },
  methods: {},
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
</style>
