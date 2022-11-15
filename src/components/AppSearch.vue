<template>
    <div class="container p-4">
        <form class="row row-cols-lg-auto g-3 align-items-center" @submit.prevent="searchCharacter">
            <div class="col-12">
                <label class="visually-hidden" for="charactername">Search Name</label>
                
                <input type="text" class="form-control" id="charactername" placeholder="Search Name">
            
            </div>

            <div class="col-12">
                <label class="visually-hidden" for="searchstatus">Search Status</label>
                <select class="form-select" id="searchstatus" v-model="search">
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

    export default {
        name: 'AppSearch',
        data() {
            return {
                statusOptions: [
                    'alive',
                    'dead',
                    'unknown'
                ],
                search: ''
            }
        },
        // props: {
        //     searchStatus: String
        // },
        methods: {
            searchCharacter(){
                this.$emit('filteredchar', this.search)
                console.log(this.search)
            },
            resetSearch() {
                this.search = '';
                this.$emit('filteredchar', this.search)
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>