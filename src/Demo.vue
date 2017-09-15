<template>
  <div id="app">

    <h1>Datepicker Examples</h1>

    <div class="example">
      <datepicker placeholder="Select Date" v-model="vModelExample" :format="'dd/MM/yyyy'" :name="'Final'" :language="'pt-br'" calendar-button="true" calendar-button-icon="fa fa-calendar" :disabled="{to: new Date(1973, 0, 5), from: new Date()}"></datepicker>
    </div>
  </div>
</template>

<script>
import Datepicker from '@/components/Datepicker'
import DateLanguages from '@/utils/DateLanguages'

const state = {
  date1: new Date()
}

export default {
  name: 'app',
  components: {
    Datepicker
  },
  data () {
    return {
      format: 'd MMMM yyyy',
      disabled: {},
      eventMsg: null,
      state: state,
      language: 'en',
      languages: DateLanguages.translations,
      vModelExample: null
    }
  },
  methods: {
    disableTo (val) {
      if (typeof this.disabled.to === 'undefined') {
        this.disabled = {
          to: null,
          from: this.disabled.from
        }
      }
      this.disabled.to = val
    },
    disableFrom (val) {
      if (typeof this.disabled.from === 'undefined') {
        this.disabled = {
          to: this.disabled.to,
          from: null
        }
      }
      this.disabled.from = val
    }
  }
}
</script>

<style>

body {
    font-family: 'Helvetica Neue Light', Helvetica, sans-serif;
    padding: 1em 2em 2em;
}
input, select {
    padding: .75em .5em;
    font-size: 100%;
    border: 1px solid #ccc;
    width: 100%
}

select {
    height: 2.5em;
}

.example {
    background: #f2f2f2;
    border: 1px solid #ddd;
    padding: 0em 1em 1em;
    margin-bottom: 2em;
}

code,
pre {
    margin: 1em 0;
    padding: 1em;
    border: 1px solid #bbb;
    display: block;
    background: #ddd;
    border-radius: 3px;
}

.settings {
    margin: 2em 0;
    border-top : 1px solid #bbb;
    background: #eee;
}

h5 {
    font-size:100%;
    padding: 0;
}

.form-group {
    margin-bottom: 1em;
}

.form-group label {
    font-size: 80%;
    display: block;
}
</style>
