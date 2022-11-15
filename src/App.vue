<template>
  <AppHeader title="Rick and Morty App"/>
  <main>
    <AppSearch @filteredchar="getCharacters"/>
    <CharactersList :characters="characterList" :loading="loading"/>
  </main>
</template>

<script>
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import CharactersList from './components/CharactersList.vue';
export default {
    components: { AppHeader, AppSearch, CharactersList },
    data(){
      return {
        apiURL: 'https://rickandmortyapi.com/api/character',
        characterList: [],
        loading: false,
        searchStatus: ''
      }
    },
    methods: {
      getCharacters(status){
        // const apiurl = (status) ? this.apiURL + '?status=' + status : this.apiURL;
        let options = null;
        if(status) {
          options = {
            params: {
              status: status
            }
          }
        }
        
        this.loading = true;
        // devo mettere l'url dell'endpoint che in qst caso è già la mia apiURL
        axios.get(this.apiURL, options).then(
          (res)=>{
            this.characterList = [...res.data.results];
            console.log(this.characterList);
            this.loading = false;
          },
        )
        .catch((error)=>{
          this.loading = false;
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