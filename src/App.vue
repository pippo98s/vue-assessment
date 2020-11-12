<template>
  <div id="app">
    <nav>
      <img alt="Vue logo" src="./assets/img/logo.png">
    </nav>
    <main>
      <section id="lato-sinistro">
        <ListaProdotti v-on:select="inserisciProdotto"/>
        <SearchBar v-if="prodottiInseriti.length > 0" :lista="prodottiInseriti"/>
      </section>
      <section id="lato-destro">
        <Frigorifero :prodotti="prodottiInseriti"/>
      </section>
    </main>
  </div>
</template>

<script>
import ListaProdotti from './components/ListaProdotti'
import Frigorifero from './components/Frigorifero'
import SearchBar from './components/SearchBar'

export default {
  name: 'App',
  components: {
    ListaProdotti,
    Frigorifero,
    SearchBar
  },
  data(){
    return{
      prodottiInseriti : []
    }
  },
  methods: {
    // grazie all'evento ricevuto da ListaProdotti individuo il prodotto che è stato selezioanto
    // e lo inserisco nell' array(this.prodottiInseriti)
    // array che passo ai componenti figli tramite props  
    inserisciProdotto(prodotto){
      if(!this.prodottiInseriti.includes(prodotto))
        this.prodottiInseriti.push(prodotto)
    }
  }

}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
nav{
  background-color: #2c3e50;
  padding: 10px;
  img{
    width: 60px;
  }
}
main{
  display: flex;
  padding: 10px;
  #lato-sinistro,
  #lato-destro{
    width: 50%;
  }
}


@media screen and (max-width: 750px) {
  main{
    flex-direction: column;
    justify-content: flex-start;
    #lato-sinistro,
    #lato-destro{
      width: 100%;
    }
  }
}
</style>
