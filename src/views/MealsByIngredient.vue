<template>
   <div class="p-8 pb-0">
    <h1 class="text-4xl font-bold mb-4 text-orange-500"> Meals for {{ ingredient.strIngredient }}</h1>
   </div>

   <Meals :meals="meals" /> 
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, ref } from 'vue';
import store from '../store';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue';

const route = useRoute();
const meals = computed(() => store.state.mealsByIngredient)
const ingredient = computed(() => store.state.ingredient)

onMounted(() => {
    store.dispatch('searchMealsByIngredient', route.params.ingredient)
})

</script>
