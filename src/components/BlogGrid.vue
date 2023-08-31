<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios'
import BlogGridItem from './BlogGridItem.vue';
import BlogDetails from './BlogDetails.vue';
defineProps(['categories'])

let latesNews = ref([]);

async function getBlog() {
    let blog = axios.get('https://basic-blog.teamrabbil.com/api/post-newest')
    blog.then((response) => {
        if (response['data']) {
            latesNews.value = response['data'];
            console.log(latesNews)
        }
    })
}
onMounted(() => {
    getBlog();
});

let detailsNewas = ref('');

function getBlogDetails(blog_id) {
    let blog = axios.get('https://basic-blog.teamrabbil.com/api/post-details/' + blog_id)
    blog.then((response) => {
        if (response['data']) {
            detailsNewas.value = response['data']['postDetails'];
            console.log(detailsNewas.value)
        }
    })
}



</script>
<template>
    <section class="py-6 sm:py-12">
        <div class="container p-6 mx-auto space-y-8">
            <div class="space-y-2 text-center">
                <h2 class="text-3xl font-bold">সাম্প্রতিক খবর</h2>
            </div>
            <div class="grid grid-cols-1 gap-x-4 gap-y-8 md:grid-cols-2 lg:grid-cols-4">
                <BlogGridItem v-for="newsItem in latesNews" :key="newsItem.id" :newsItem="newsItem"
                    :category="categories[newsItem.category_id] ? categories[newsItem.category_id] : ''"
                    @click.prevent="getBlogDetails(newsItem.id)" />
            </div>

            <BlogDetails v-show="detailsNewas.length > 0" />


            <div v-show="latesNews.length == 0" class="flex items-center justify-center ">
                <div class="w-40 h-40 border-t-4 border-b-4 border-green-900 rounded-full animate-spin"></div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped></style>