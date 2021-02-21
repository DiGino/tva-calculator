<template>
  <div class="tva">

    <h1>{{msg}}</h1>
      <input type="number" class="form" v-model.number="valeurHT">
      <label class="currency">FCFA HT</label>
    <div class="taux">
      <h2>Choisissez le taux</h2>
      <input type="radio" class="form-radio" name="tva" id="20" checked value="0.2" v-model="taux">
      <label class="form-label" for="20">20 %</label>

      <input type="radio" class="form-radio" name="tva" id="18" value="0.18" v-model="taux">
      <label class="form-label" for="18">18 %</label>

      <input type="radio" name="tva" id="10" value="0.1" v-model="taux">
      <label class="form-label" for="10">10 %</label>

      <input type="radio" class="form-radio" name="tva" id="5" value="0.05" v-model="taux">
      <label class="form-label" for="5">5 %</label>
    </div>
    <div class="results">
      <span class="block">Montant TTC: <b>{{valeurTTC | twoDecimals}}</b> FCFA</span>
      <span class="block">TVA appliquée: <b>{{tva_appliquee | twoDecimals}}</b> FCFA</span>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Tva',
  props: {
      msg: String
  },
  filters: {
    twoDecimals: function(value) {
      return parseFloat(value).toFixed(2);
    }
  },
  data: function() {
    return {
      valeurHT: 0,
      taux: '0.2'
    }
  },
  mounted() {
    if (localStorage.valeurHT) {
      this.valeurHT = localStorage.valeurHT;
    }
  },
  watch: {
    valeurHT(newvaleurHT) {
    localStorage.valeurHT = newvaleurHT;
  }
  },
  computed: {
    valeurTTC: function() {
      return parseFloat(this.valeurHT) + this.tva_appliquee;
    },
    tva_appliquee: function() {
      return parseFloat(this.valeurHT * this.taux);
    }
  }
}

</script>

<style scoped>
  input {
    margin: 1em;
  }

  .form {
	width: 16em;
	height: 2em;
  }

  .block {
    display: block;
    padding: 0.2em 0;
  }

  .tva {
    background: #ecf2f2;
    padding: 2em;
    border-radius: 1em
  }

  .results {
    margin-top: 1em
  }

</style>
