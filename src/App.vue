<template>
  <input type="text" v-model="input">

  <div class="grid-container">
    <div class="grid-row" v-for="row in btns" :key="row">
      <div class="grid-cell" v-for="btn in row" :key="btn">
        <button v-if="btn === 'c'" @click="backspace">
          {{ btn }}
        </button>
        <button v-else-if="btn === '='" @click="exec">
          {{ btn }}
        </button>
        <button v-else @click="click(btn)">
          {{ btn }}
        </button>
      </div>

    </div>
  </div>
  <h1>{{ result }}</h1>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    input: '',
    result: '',
    btns: [
      [7, 8, 9, '+'],
      [4, 5, 6, '-'],
      [1, 2, 3, '*'],
      ['=', 0, 'c', '/']
    ]
  }),
  methods: {
    click (e) {
      this.input += e
    },
    backspace () {
      if (this.input) {
        this.input = this.input.slice(-1)
      }
    },
    exec () {
      // const num = parseInt(this.number) || 0
      // eslint-disable-next-line no-eval
      this.result = eval(this.input)
    }
  },
  components: {}

}
</script>
