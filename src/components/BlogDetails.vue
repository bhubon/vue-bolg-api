<script setup>
defineProps(['detailsNewas'])
</script>

<template>
    <div>
        <a href="/vue/blog" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mb-4 inline-block">Back</a>
        <article class="flex flex-col border-[1px] border-black-100 rounded-md">
            <a rel="noopener noreferrer" href="#" aria-label="Te nulla oportere reprimique his dolorum">
                <img class="object-cover w-full h-52 dark:bg-gray-500 custom-border h-auto" :src="detailsNewas.img">
            </a>
            <div class="flex flex-col flex-1 p-6">
                <a rel="noopener noreferrer" href="#" :aria-label="detailsNewas.title"></a>
                <a href="">
                    <h3 class="flex-1 py-2 text-lg font-semibold leadi">{{ detailsNewas.title }}</h3>
                </a>
                <p>{{ detailsNewas.content }}</p>
            </div>
        </article>
    </div>
</template>

<style scoped></style>