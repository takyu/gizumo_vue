<template>
  <div>
    <h1>-- slot --</h1>
    <!-- <child-component v-show="isShow"></child-component> -->
    <hr />
    <child-component v-show="isShow">
      <!-- <template v-slot:head>
        <p>head slot</p>
      </template>
      <template v-slot:default>
        <p>main slot</p>
        <p>main slot2</p>
      </template>
      <template v-slot:foot>
        <p>foot slot</p>
      </template> -->
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
    <!-- <template v-for="item in items">
      <child-component :key="item.id">
        <span>slot content</span>
      </child-component>
    </template> -->
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
