<template>
    <div class="w-96 mx-auto mt-6 pt-8">
        <h1 class="text-lg">Create Post</h1>
        <div class="mb-4">
            <Link :href="route('post.index')" class="text-red-600 text-sm">Back on page</Link>
        </div>


        <form @submit.prevent="store">
            <div class="mb-4">
                <input v-model="title" class="w-full rounded-full border-gray-300" type="text" placeholder="Title">
                <div v-if="errors.title" class="text-red-600 text-sm">{{ errors.title}}</div>
            </div>

            <div class="mb-4">
                <textarea v-model="content" class="w-full rounded-lg border-gray-300" placeholder="Content" ></textarea>
                <div v-if="errors.content" class="text-red-600 text-sm">{{ errors.content}}</div>
            </div>

            <div class="mb-6">
                <button class="ml-auto hover:bg-white hover:text-gray-500 block p-2 w-32 border-2 border-sky-500 bg-sky-500 rounded-full text-center text-white" type="submit">Add Post</button>
            </div>
        </form>
    </div>
</template>

<script>
import {Link} from '@inertiajs/vue3'
export default {
    name: "Index",
    components: {
        Link
    },

    props: [
        'errors'
    ],

    data() {
      return {
          title: '',
          content: '',
      }
    },

    methods: {
        store() {
            this.$inertia.post('/posts', {title: this.title, content: this.content})
        }
    }
}
</script>

<style scoped>

</style>
