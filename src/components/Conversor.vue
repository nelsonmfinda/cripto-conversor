<template>
  <div class="container">
    <h1 class="h1">Criptocurrency Conversor</h1>
    <div class="columns">
      <div class="column is-three-fifths">
        <form>
          <div class="field">
            <label class="label">From</label>
            <div class="control">
              <input
                v-model="from"
                class="input"
                type="text"
                placeholder="Text input"
              />
            </div>
            <p class="help">This is a help text</p>
          </div>
          <div class="field">
            <label class="label">To</label>
            <div class="control">
              <input
                v-model="to"
                class="input"
                type="text"
                placeholder="Text input"
              />
            </div>
            <p class="help">This is a help text</p>
          </div>
          <div class="field">
            <label class="label">Amount</label>
            <div class="control">
              <input
                v-model="amount"
                class="input"
                type="text"
                placeholder="Text input"
              />
            </div>
            <p class="help">This is a help text</p>
          </div>
          <div class="control">
            <button
              @click.prevent="convertCurrency()"
              class="button is-primary"
            >
              Submit
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Conversor",
  props: {},
  data: function() {
    return {
      from: 0,
      to: 0,
      result: "",
      amount: ""
    };
  },
  methods: {
    async convertCurrency() {
      try {
        this.axios
          .get(
            `/convert?q=${this.from}_${this.to}&compact=ultra&apiKey=${process.env.API_KEY}`
          )
          .then(response => {
            // console.log(response);
            this.result = response;
          });
      } catch (e) {
        console.log(e);
      }
    },
    async getCurrencies() {
      try {
        this.axios
          .get(`/currencies?apiKey=${process.env.API_KEY}`)
          .then(response => {
            // console.log(response);
            this.result = response;
          });
      } catch (e) {
        console.log(e);
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
