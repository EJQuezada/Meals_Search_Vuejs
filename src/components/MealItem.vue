<template>
    <div 
        class="bg-white shadow rounded-xl"
    >
        <router-link :to="{name: 'mealDetails', params: {id: meal.idMeal}}">
            <img 
                :src="meal.strMealThumb" 
                :alt="meal.strMeal" 
                class="rounded-t-xl w-full h-48 object-cover"
            />
        </router-link>
        <div class="p-3">
            <h3 class="font-bold">{{ meal.strMeal }}</h3>
            <p class="mb-4">
                Click on the <b>image</b> to view ingredients list and preparation instructions. Alternatively, click the <b>button</b> below to view the cooking video for this recipe on YouTube.
            </p>
            <div class="flex items-center justify-between">
                <YouTubeButton :href="meal.strYoutube">
                    YouTube
                </YouTubeButton>
            </div>
        </div>
    </div>
</template>

<script setup>
import YouTubeButton from './YouTubeButton.vue';


const { meal } = defineProps({
    meal: {
        required: true,
        type: Object
    }
})
</script>