<template>
    <div>
        <p>name : {{ this.userInfo.id }}</p>
        <p>karma : {{ this.userInfo.karma }}</p>
        <p>created: {{ this.userInfo.created }}</p>
        <p>about: {{ this.userInfo.about }}</p>
    </div>
</template>

<script>
export default {
    computed: {
        userInfo() {
            return this.$store.state.user;
        }
    },
    created() {
        const userName = this.$route.params.id;
        // axios.get(`https://api.hnpwa.com/v0/user/${userName}.json`);
        this.$store.dispatch('FETCH_USER', userName);
    }
}
</script>

<style>

</style>