<template>
<div class="w-25">
    <input v-model="email" type="email" placeholder="email" class="form-control mt-3 mb-3">
    <input v-model="password" type="password" placeholder="password" class="form-control mb-3">
    <input @click.prevent="login" type="submit" value="login" class="btn btn-primary">
</div>
</template>

<script>

export default {
    name: "Login",

    data() {
        return {
            email: null,
            password: null,
        }
    },

    methods: {
        login() {
            axios.get('/sanctum/csrf-cookie').then(response => {
                axios.post('/login', { email: this.email, password: this.password })
                    .then( r => {
                        localStorage.setItem('x_xsrf_token', r.config.headers['X-XSRF-TOKEN'])
                        this.$router.push({name: 'user.personal'})
                    })
            });
        }
    }
}
</script>

<style scoped>

</style>
