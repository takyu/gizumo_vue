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
    <hr />
    <form action="">
      <div>
        <span>名前： </span>
        <input type="text" v-model="form.name" />
        <!-- <input
          type="text"
          :value="form.name"
          @input="form.name = $event.target.value"
        /> -->
        <p>名前： {{ getInputName }}</p>
      </div>
      <div>
        <span>性別：</span>
        <label>
          男性
          <input type="radio" name="sex" value="male" v-model="form.sex" />
        </label>
        <label>
          女性
          <input type="radio" value="female" name="sex" v-model="form.sex" />
        </label>
        <p>性別： {{ getRadioValue }}</p>
      </div>
      <div>
        <select v-model="form.selected">
          <option disabled value="">-- 出身地を選択してください --</option>
          <option>東京都</option>
          <option>埼玉県</option>
          <option>神奈川県</option>
          <option>千葉県</option>
        </select>
        <p>出身地: {{ getSelectValue }}</p>
      </div>
      <div>
        <select v-model="form.selected">
          <option disabled value="">-- 出身地を選択してください --</option>
          <option
            v-for="option in form.options"
            :value="option.value"
            :key="option.id"
          >
            {{ option.value }}
          </option>
        </select>
        <p>出身地: {{ getSelectValue }}</p>
      </div>
      <div>
        <label>
          <input type="checkbox" v-model="form.checked" />
          20歳以上
        </label>
        <p>チェックボックス： {{ getCheckBoxValue }}</p>
      </div>
    </form>
  </div>
</template>

<script>
  import ChildComponent from 'Components/ChildComponent';
  export default {
    //es6のメソッド記法
    data() {
      return {
        message: '-- form binding --',
        classObject: {
          'is-large': false,
        },
        inputText: '',
        leads: {
          message: '<span>Hello Vue</span>',
          description: '',
        },
        form: {
          name: '',
          sex: '',
          selected: '',
          options: [
            {
              id: this.$uuid.v4(),
              value: '東京都',
            },
            {
              id: this.$uuid.v4(),
              value: '埼玉県',
            },
            {
              id: this.$uuid.v4(),
              value: '神奈川県',
            },
            {
              id: this.$uuid.v4(),
              value: '千葉県',
            },
          ],
          checked: false,
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
      getInputName() {
        return this.form.name;
      },
      getRadioValue() {
        return this.form.sex;
      },
      getSelectValue() {
        return this.form.selected;
      },
      getCheckBoxValue() {
        return this.form.checked;
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
