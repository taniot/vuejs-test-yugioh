<script>
import axios from 'axios';
import {store} from './store';
import SearchApp from './components/SearchApp.vue';
export default {
  name: 'App',
  components: {
    SearchApp
  },
  data() {
    return {
      store,
      archetypes: [],
      urlCards: 'https://db.ygoprodeck.com/api/v7/cardinfo.php',
      urlArc: 'https://db.ygoprodeck.com/api/v7/archetypes.php'
    }
  },
  created() {
    console.log('created');
    axios.get(this.urlArc)
      .then((response) => {
        console.log(response.data);
        this.archetypes = response.data;
      });
  },
  methods: {
    search() {
      console.log('ho ricevuto il tuo evento: ricerca');
      console.log(store.searchKey);

      if(store.searchKey === '') {
        //TODO: svuoto risultati ricerca
        return;
      }

      //chiamata cards
      axios.get(this.urlCards, {
        params: {
          archetype: store.searchKey
        }
      })
      .then((response) => {
        console.log(response.data);
      });
    }
  }
}
</script>

<template>
  <h1>Test APP Yu-Gi-Oh</h1>
  <SearchApp @ricerca="search" :archetypes="archetypes" />
</template>


<style lang="scss">
//versione 1 - inclusione via app.vue
// @use './assets/scss/main.scss' as *;
</style>
