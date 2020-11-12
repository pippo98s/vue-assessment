<template>
  <section id="searchbar">
    <h2>Prodotti inseriti</h2>
    <input  type="text"
            placeholder="cerca prodotto"
            v-model.trim="textInput"
            v-on:input="ricercaProdotti">
    <div id="contenitore-ricerca">
      <ul>
        <li v-for="prodotto in prodottiTrovati" :key="prodotto">
        {{prodotto}}
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: 'SearchBar',
  props: {
    lista : Array
  },
  data(){
    return{
      textInput : '',
      prodottiTrovati : []
    }
  },
  methods: {

    ricercaProdotti(){
      // svuoto l'array per eliminare le ricerche precedenti
      this.prodottiTrovati = []

      if(this.textInput !== ''){
        // ciclo nella lista dei prodotti presenti nel frigorifero
        this.lista.forEach(prodotto=>{
          // se il nome del prodotto include il testo dell'input(this.textInput)
          // inserisco il prodotto nel nuovo array(this.prodottiTrovati) 
          if(prodotto.nome
                          .toLowerCase()
                          .trim() 
                          .includes(this.textInput.toLowerCase())
          ){
            this.prodottiTrovati.push(prodotto.nome)
          }
        })
      }
    },
  }
  
}
</script>

<style lang="scss" scoped>
#searchbar{
  margin-left: 20px;
  margin-bottom: 20px;
  text-align: center;
  input{
    width: 200px;
    display: block;
    margin: auto;
    &:focus{
      outline-color: #42b983;
    }
  }
  #contenitore-ricerca{
    position: relative;
    width: 200px;
    margin: auto;
  }
  ul{
    left: 0;
    list-style-type: none;
    max-height: 100px;
    overflow-x: hidden;
    overflow-y: auto;
    position: absolute;
    top: 0;
    width: 200px;
    z-index: 1;
    li{
      background-color: #42b983;
      color: #fff;
      padding: 5px;
      width: 200px;
      text-align: left;
    }
  }
}
</style>