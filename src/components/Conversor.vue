<template>
  <div class="container">
    <form class="col-md-6 mt-5 offset-3">
      <div class="form-group">
        <label class="float-left" for="amount">Amount</label>
        <input type="text" class="form-control" id="amount" v-model="amount">
      </div>
      <div class="form-group">
        <label class="float-left" for="from">From</label>
        <select v-model="from" class="form-control" id="from">
          <option v-for="currency in currencies"
                  :value="currency.id"
                  :key="currency.id"
          >
          {{ currency.currencyName }}
          </option>
        </select>
      </div>
      <div class="form-group">
        <label class="float-left" for="to">To</label>
        <select v-model="to" class="form-control" id="to">
          <option v-for="currency in currencies"
                  :value="currency.id"
                  :key="currency.id"
          >
            {{ currency.currencyName }}
          </option>
        </select>
      </div>
      <div class="form-group">
        <p class="font-weight-bold p-2 result">{{ calculateConversion }}</p>
      </div>
      <button @click.prevent="convertCurrency()" class="btn btn-primary btn-block">Convert</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Conversor',
  props: {},
  data: function () {
    return {
      from: 'BTC',
      to: 'USD',
      currencies: '',
      amount: 0,
      result: 0
    }
  },
  computed: {
    calculateConversion: function () {
      return (Number(this.amount) * this.result).toFixed(3)
    }
  },
  methods: {
    async convertCurrency () {
      const query = `${this.from}_${this.to}`
      try {
        this.axios
          .get(
            `/convert?q=${query}&compact=ultra&apiKey=${process.env.VUE_APP_TOKEN}`
          )
          .then(response => {
            this.result = response.data[query]
            console.log(response.data[query])
          })
      } catch (e) {
        console.log(e)
      }
    },
    async getCurrencies () {
      try {
        this.axios
          .get(`/currencies?apiKey=${process.env.VUE_APP_TOKEN}`)
          .then(response => {
            this.currencies = response.data.results
            console.log(this.currencies)
          })
      } catch (e) {
        console.log(e)
      }
    }
  },
  created () {
    this.getCurrencies()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .page-title {
    margin-top: 20px;
    text-transform: uppercase;
    padding: 3em;
  }

  .result {
    font-size: 2em;
  }
</style>
