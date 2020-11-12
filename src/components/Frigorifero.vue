<template> 
  <section id="frigorifero">
    <h2>Frigorifero</h2>
    <div id="verdure">
      <div class="contenitore-img">
        <img src="../assets/img/verdure.png" alt="verdure">
      </div>
      <ul>
        <li v-for="prodotto in filtroCategoria('verdure')" :key="prodotto.nome" >
            {{prodotto.nome}}
        </li>
      </ul>
    </div>
    <div id="salumi">
      <div class="contenitore-img">
        <img src="../assets/img/salumi.png" alt="salumi">
      </div>
      <ul>
        <li v-for="prodotto in filtroCategoria('salumi')" :key="prodotto.nome" >
            {{prodotto.nome}}
        </li>
      </ul>
    </div>
    <div id="formaggi">
      <div class="contenitore-img">
        <img src="../assets/img/formaggi.png" alt="salumi">
      </div>
      <ul>
        <li v-for="prodotto in filtroCategoria('formaggio')" :key="prodotto.nome" >
            {{prodotto.nome}}
        </li>
      </ul>
    </div>
    <div id="bibite">
      <div class="contenitore-img">
        <img src="../assets/img/bibite.png" alt="salumi">
      </div>
      <ul>
        <li v-for="prodotto in filtroCategoria('bibite')" :key="prodotto.nome" >
            {{prodotto.nome}}
        </li>
      </ul>
    </div>
    <div id="altro">
      <div class="contenitore-img">
        <img src="../assets/img/altro.png" alt="salumi">
      </div>
      <ul>
        <li v-for="prodotto in filtroCategoria('altro')" :key="prodotto.nome" >
            {{prodotto.nome}}
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name : 'Frigorifero',
  props: {
    prodotti: Array
  },
  methods:{
    // per ogni categoria ottengo un nuovo array 
    // che contiene solo i prodotti della stessa categoria passata come parametro
    filtroCategoria(categoria) {
      return this.prodotti.filter(i => i.categoria === categoria)
    }
  }
}
</script>

<style lang='scss' scoped>
#frigorifero{
  background-color: rgb(206, 206, 206);
  border-radius: 5px;
  padding: 10px;
  h2{
    margin: 10px;
    text-align: center;
  }
  &>div{
    border-radius: 5px;
    margin: 5px 0;
    min-height: 80px;
    display: flex;
    .contenitore-img{
      align-items: center;
      border-right: 1px solid #000;
      display: flex;
      padding: 20px;
      position: relative;
      text-align: center;
      width: 80px;
      img{
        width: 40px;
      }
    }
    ul{
      list-style-type: none;
      padding: 5px;
      li{
        background-color: #2c3e50;
        border-radius: 5px;
        color: #fff;
        display: inline-block;
        margin: 5px;
        padding: 10px;
        width: max-content;
      }
    }
  }
  #verdure{
    background-color: #008000;
  }
  #salumi{
    background-color: #ff0000;
  }
  #formaggi{
    background-color: #ffff00;
  }
  #bibite{
    background-color: #fff;
  }
  #altro{
    background-color: #fa8072;
  }
}


</style>