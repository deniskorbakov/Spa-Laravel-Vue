<template>
    <div class="w-96 mx-auto mt-6 pt-8">
        <h1 class="text-lg mb-8">Page For Posts</h1>
        <div class="mb-6">
            <Link :href="route('post.create')" class="hover:bg-white hover:text-gray-500 block p-2 w-32 border-2 border-sky-500 bg-sky-500 rounded-full text-center text-white">Add Post</Link>
        </div>

        <div v-if="posts">
            <div class="mt-8 pt-8 border-t border-gray-300" v-for="post in posts">
                <div>id: {{ post.id}}</div>
                <div>title: {{ post.title}}</div>
                <div>content: {{ post.content}}</div>
                <div class="text-sm text-right mt-2">{{ post.date}}</div>
                <div class="text-sm text-right mt-2">
                    <Link class="text-sky-500" :href="route('post.show', post.id)">Show Page</Link>
                </div>

                <div class="text-sm text-right mt-2">
                    <Link class="text-sky-500" :href="route('post.edit', post.id)">Edit Page</Link>
                </div>

                <div class="text-sm text-right mt-2">
                    <p @click="deletePost(post.id)" class="cursor-pointer text-red-500">Delete Page</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import {Link} from '@inertiajs/vue3'
export default {
    name: "Index",

    props: [
        'posts'
    ],

    components: {
        Link
    },

    methods: {
        deletePost(id) {
            this.$inertia.delete(`/posts/${id}`)
        }
    }
}
</script>

<style scoped>

</style>
