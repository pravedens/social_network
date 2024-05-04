<template>
    <div class="w-96 mx-auto">
        <div v-if="users">
            <div class="flex justify-between items-center mb-6 pb-6 border-b border-gray-400" v-for="user in users">
                <router-link :to="{name: 'user.show', params: {id: user.id}}">
                    <p>{{ user.id }}</p>
                    <p>{{ user.name }}</p>
                    <p>{{ user.email }}</p>
                </router-link>
                <div>
                    <a @click.prevent="toggleFollowing(user)"
                       :class="['block p-2 w-32 text-center rounded-3xl', user.is_followed ? 'bg-white text-sky-500 hover:bg-white hover:border hover:border-green-600 hover:text-green-600 ml-auto' : 'bg-sky-500 text-white hover:bg-white hover:border hover:border-green-600 hover:text-green-600 ml-auto']" href="#">
                        {{  user.is_followed ? 'Отписаться' : 'Подписаться'}}</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: "Index",

    data() {
        return {
            users: []
        }
    },

    mounted() {
        this.getUsers()
    },

    methods: {
        getUsers() {
            axios.get('/api/users')
                .then( res => {
                    this.users = res.data.data
                })
        },

        toggleFollowing(user) {
            axios.get(`/api/users/${user.id}/toggle_following`)
                .then( res => {
                    user.is_followed = res.data.is_followed
                })
        }
    }
}
</script>

<style scoped>

</style>
