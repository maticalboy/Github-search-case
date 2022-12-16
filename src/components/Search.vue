<template>
    <section class="jumbotron">
        <h3 class="jumbotron-heading">Search Github Users</h3>
        <div>
            <input type="text" placeholder="enter the name you search" />&nbsp;
            <button @click="searchUsers">Search</button>
        </div>
    </section>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Search',
    data(){
        return {
            keyWord:'',
        }
    },
    methods: {
        searchUsers(){
            axios.get(`https://api.github.com/search/users?q=${this.kewWord}`).then(
                response=>{
                    console.log(response.data)
                    let userList=response.data.items
                    this.$bus.$emit('getList',userList)
                },
                error=>{
                    console.log(error.message)
                }
            )
        }
    },
}
</script>

<style>

</style>