<template>
    <div class="container p-4">
        <form class="row row-cols-lg-auto g-3 align-items-center" @submit.prevent="searchCharacter">
            <div class="col-12">
                <label class="visually-hidden" for="charactername">Search Name</label>
                
                <input type="text" class="form-control" id="charactername" placeholder="Search Name">
            
            </div>

            <div class="col-12">
                <label class="visually-hidden" for="searchstatus">Search Status</label>
                <select class="form-select" id="searchstatus" v-model="store.searchStatus">
                <option selected>Choose...</option>
                <option :value="status" v-for="(status, index) in statusOptions" :key="index">{{status}}</option>
                </select>
            </div>

            <div class="col-12">
                <button type="submit" class="btn btn-primary">Search</button>
            </div>

            <div class="col-12">
                <button type="reset" class="btn btn-primary" @click="resetSearch">Reset</button>
            </div>
        </form>
    </div>
</template>

<script> 
import {store} from '../store.js'
    export default {
        name: 'AppSearch',
        data() {
            return {
                store,
                statusOptions: [
                    'alive',
                    'dead',
                    'unknown'
                ],
            }
        },
        // props: {
        //     searchStatus: String
        // },
        methods: {
            searchCharacter(){
                this.$emit('filteredchar')
            },
            resetSearch() {
                store.searchStatus= ''; // oppure: this.store.searchStatus= '';
                this.$emit('filteredchar')
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>