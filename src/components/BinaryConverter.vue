<template>
  <div class="section">
    <div class="buttons is-centered">
      <button class="button" v-on:click="toggle(7)">{{ digits.digit8 }}</button>
      <button class="button" v-on:click="toggle(6)">{{ digits.digit7 }}</button>
      <button class="button" v-on:click="toggle(5)">{{ digits.digit6 }}</button>
      <button class="button" v-on:click="toggle(4)">{{ digits.digit5 }}</button>
      <button class="button" v-on:click="toggle(3)">{{ digits.digit4 }}</button>
      <button class="button" v-on:click="toggle(2)">{{ digits.digit3 }}</button>
      <button class="button" v-on:click="toggle(1)">{{ digits.digit2 }}</button>
      <button class="button" v-on:click="toggle(0)">{{ digits.digit1 }}</button>
    </div>
    <h3 id="decimal">Valeur décimale: {{ result }}</h3>
  </div>
</template>

<script>
export default {
  name: 'BinaryConverter',
  data() {
    return {
      digits: {
        digit1: 0,
        digit2: 0,
        digit3: 0,
        digit4: 0,
        digit5: 0,
        digit6: 0,
        digit7: 0,
        digit8: 0,
      },
    };
  },
  methods: {
    toggle(index) {
      const key = Object.keys(this.digits)[index];
      this.digits[key] = 1 - this.digits[key];
    },
  },
  computed: {
    result() {
      let res = 0;
      const keys = Object.keys(this.digits);
      for (let i = 0; i < keys.length; i += 1) {
        res += this.digits[keys[i]] * (2 ** i);
      }
      return res;
    },
  },
};
</script>

<style scoped lang="scss">
  button {
    padding: 13px 25px 55px 25px;
    margin: 5px;
    font-size: 2rem;
    user-select: none;

  }
  h3 {
    font-size: 2rem;
    text-align: center;
  }
</style>
