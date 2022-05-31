<template>
  <div>
    <button @click="incrementCount">Add to count</button>
    <p>{{ count }}回クリックされました</p>
  </div>
</template>

<script>
  import { mapState, mapActions } from 'vuex';

  export default {
    computed: {
      // ...mapState(['count']),

      /* count module */
      ...mapState('count', {
        count: (state) => state.count,
        // count: function (state) {
        //   return state.count;
        // },
      }),
    },
    methods: {
      // ...mapActions(['incrementCount']),
      // incrementCount() {
      //   // mutation
      //   // this.$store.commit('incrementCount');
      //   // action -> mutation
      //   // this.$store.dispatch('incrementCount');
      // },

      /* count module */
      ...mapActions('count', ['incrementCount']),
    },
  };
</script>
