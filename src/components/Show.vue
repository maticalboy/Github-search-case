<template>
    <div>
        <h2 v-if="isFirst">欢迎</h2>
        <div class="row">
            <div class="card" v-for="x in userList" :key="x.login">
                <a :href="x.html_url" target="_blank">
                    <img :src="x.avatar_url" style='width: 100px' />
                </a>
                <p class="card-text">{{ x.login }}</p>
            </div>
        </div>
    </div>

</template>

<script>
export default {
    name: 'ShowVue',
    data() {
        return {
            isFirst: true,
            isLoading: false,
            errmsg: '',
            userList: [

            ]
        }
    },
    mounted() {
        this.$bus.$on('getList', (users) => {
            this.isFirst = false

            this.userList = users


        })
    }
}
</script>

<style>

</style>