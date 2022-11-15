<template>
    <div class="container">
        <div v-if="store.loading">Sto caricando...</div>
        <div class="row" v-if="!store.loading">
            <div class="col-12 col-sm-6 col-md-4 col-lg-3">
                <div class="character" v-for="(item, index) in store.characterList" :key="item.id">
                    <img :src="item.image" :alt="item.name">
                    <h1>{{item.name}}</h1>
                    <h2>{{item.status}}</h2>
                    <h3>{{item.species}}</h3>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import {store} from '../store';
    export default {
        name: 'CharactersList',
        data(){
            return {
                store
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>