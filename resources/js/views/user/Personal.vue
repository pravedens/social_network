<template>
    <div class="w-96 mx-auto">
        <div>
            <div>
                <input v-model="title" class="w-96 mb-3 rounded-3xl border border-slate-400 p-2" type="text" placeholder="title">
            </div>
            <div>
                <textarea v-model="content" class="w-96 mb-3 rounded-3xl border border-slate-400 p-2" placeholder="content"></textarea>
            </div>
            <div class="flex mb-3">
                <a href="#" class="block p-2 w-32 text-center rounded-3xl bg-green-600 text-white hover:bg-white hover:border hover:border-green-600 hover:text-green-600">Publish</a>
            </div>
            <div v-if="image">
                <img :src="image.url" alt="preview">
            </div>
            <div class="flex mb-3 items-center mt-4">
                <div class="mr-4">
                    <input @change="storeImage" ref="file" type="file" class="hidden">
                    <a href="#" class="block p-2 w-32 text-center rounded-3xl bg-sky-500 text-white hover:bg-white hover:border hover:border-green-600 hover:text-green-600 ml-auto" @click.prevent="selectFile()">Image</a>
                </div>
                <div>
                    <a @click.prevent="image = null" href="#">Cancel</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Personal",

    data() {
        return {
            title: '',
            content: '',
            image: null,
        }
    },

    methods: {
        selectFile() {
            this.fileInput = this.$refs.file;
            this.fileInput.click();
        },

        storeImage(e) {
            const file = e.target.files[0]
            const formData = new FormData()
            formData.append('image', file)

            axios.post('/api/post_image', formData)
                .then(res => {
                    this.image = res.data.data
                })
        }
    }
}
</script>

<style scoped>

</style>
