<template>
  <section id="lista">
    <h2>Prodotti da inserire</h2>
    <ul>
      <li v-for='prodotto in prodotti' :key="prodotto.nome">
        <button v-on:click="emit(prodotto)">
          {{prodotto.nome}}
        </button>
      </li>
    </ul>
    <Alert  class="text-center"
            type="success"
            v-if="prodotti.length == 0">
      Hai inserito tutti i prodotti nel frigorifero
    </Alert>
    
  </section>
</template>

<script>
import { Alert } from 'uiv'
import listaProdotti from '../assets/data/lista-prodotti'
export default {
  name: 'ListaProdotti',
  components : {
    Alert
  },
  data(){
    return{
      prodotti : listaProdotti.prodotti
    }
  },
  methods: {

    emit(prodotto){
      // tramite $emit passo il prodotto cliccato al componente padre
      this.$emit('select' , prodotto)

      // ciclo nell'array dei prodotti per eliminare il prodotto selezioanto
      // quando l'array è vuoto indico all'utente che tutti i prodotti
      // sono stati correttamente aggiunti ai propri ripiani
      for(let i = 0; i < this.prodotti.length; i++){
        if(this.prodotti[i] == prodotto){
          this.prodotti.splice(i,1)
          return
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
#lista{
  width: 100%;
  padding: 10px;
  h2{
    text-align: center;
    margin: 10px 0;
  }
  ul{
  list-style-type: none;
    li {
      margin: 10px 0;
      text-align: center;
      button {
        background-color: #2c3e50;
        border: 0;
        border-radius: 5px;
        color: #42b983;
        cursor: pointer;
        padding: 10px;
        transition: all .3s;
        width: 80%;
        &:hover{
          background-color: #42b983;
          color: #2c3e50;
        }
      } 
    } 
  }
}

@media screen and (max-width: 750px) {
  #lista{
    li{
      width: 100%;
    }
  }
}
</style>
