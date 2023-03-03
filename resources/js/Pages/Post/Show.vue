<template>
    <div class="w-96 mx-auto mt-6 pt-8">
        <h1 class="text-lg mb-8">Page For Post</h1>
        <div class="mb-6">
            <Link :href="route('post.index')" class="text-red-600 text-sm">Back on page</Link>
        </div>

        <div v-if="post">
            <div class="mt-8 pt-8 border-t border-gray-300">
                <div>id: {{ post.id}}</div>
                <div>title: {{ post.title}}</div>
                <div>content: {{ post.content}}</div>
                <div class="text-sm text-right mt-2">{{ post.date}}</div>
            </div>
        </div>
    </div>
</template>

<script>
import {Link} from '@inertiajs/vue3'
export default {
    name: "Index",

    props: [
        'post'
    ],

    components: {
        Link
    }
}
</script>

<style scoped>

</style>
