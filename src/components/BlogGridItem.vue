<script setup>
import { defineProps } from 'vue';
defineProps(['newsItem','category'])
</script>
<template>
    <article class="flex flex-col border-[1px] border-black-100 rounded-md">
        <a rel="noopener noreferrer" href="#" aria-label="Te nulla oportere reprimique his dolorum">
            <img alt="" class="object-cover w-full h-52 dark:bg-gray-500 custom-border"
                :src="newsItem.img">
        </a>
        <div class="flex flex-col flex-1 p-6">
            <a rel="noopener noreferrer" href="#" :aria-label="newsItem.title"></a>
            <a rel="noopener noreferrer" href="#"
                class="text-xs tracki uppercase hover:underline dark:text-violet-400">{{ category['name'] ? category['name'] : '' }}</a>
            <a href=""><h3 class="flex-1 py-2 text-lg font-semibold leadi">{{ newsItem.title }}</h3></a>
            <div class="flex flex-wrap justify-between pt-3 space-x-2 text-xs dark:text-gray-400">
                <span>{{ newsItem.created_at }}</span>
            </div>
        </div>
    </article>
</template>

<style scoped>
.custom-border{
    border-radius: 4px 4px 0 0;
}
</style>