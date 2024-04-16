<template>
    <div class="w-96 mx-auto">
        <div>
            <div>
                <input v-model="title" class="w-96 mb-3 rounded-3xl border border-slate-400 p-2" type="text" placeholder="title">
            </div>
            <div>
                <textarea v-model="content" class="w-96 mb-3 rounded-3xl border border-slate-400 p-2" placeholder="content"></textarea>
            </div>
            <div>
                <a href="#" class="block p-2 w-32 text-center rounded-3xl bg-green-600 text-white hover:bg-white hover:border hover:border-green-600 hover:text-green-600">Publish</a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Personal"
}
</script>

<style scoped>

</style>
