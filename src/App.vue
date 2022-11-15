<template>
  <AppHeader title="Rick and Morty App"/>
  <main>
    <AppSearch @filteredchar="getCharacters"/>
    <CharactersList />
  </main>
</template>

<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import CharactersList from './components/CharactersList.vue';
import {store} from './store';
export default {
    components: { AppHeader, AppSearch, CharactersList },
    data(){
      return {
        store,
        endpoint: 'character',
      }
    },
    methods: {
      getCharacters(){
        // const apiurl = (status) ? this.apiURL + '?status=' + status : this.apiURL;
        let options = null;
        if(store.searchStatus) {
          options = {
            params: {
              status: store.searchStatus
            }
          }
        }
        
        store.loading = true;
        const apiurl = store.apiURL + this.endpoint
        // devo mettere l'url dell'endpoint che in qst caso è già la mia apiURL
        axios.get(apiurl, options).then(
          (res)=>{
            store.characterList = [...res.data.results];
            console.log(store.characterList);
            store.loading = false;
          },
        )
        .catch((error)=>{
          store.loading = false;
          console.log(error.response.status);
        })
      }
    },
    created(){
      this.getCharacters()
    }
}
</script>

<style lang="scss" scoped>


</style>