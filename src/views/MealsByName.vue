<template>
    <div class="p-8 pb-0">
        <h1 class="text-4xl font-bold mb-4 text-orange-500">
            Search Meals By Name
        </h1>
    </div>
    <div class="p-8 pb-3 ">
        <input type="text" class="rounded border-2 border-gray-200 w-full" placeholder="Search for meals" v-model="keyword"
            @change="searchMeals">
    </div>
    <Meals :meals="meals"></Meals>
</template>
<script setup>

import store from "../store";
import { computed } from "@vue/reactivity";
import { ref, onMounted } from 'vue';
import { useRoute } from "vue-router";

import Meals from "../components/Meals.vue";

const router = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals)

function searchMeals() {
    if (keyword.value) {
        store.dispatch('searchMeals', keyword.value)
    } else {
        store.commit('setSearchedMeals', [])
    }

}

onMounted(() => {
    keyword.value = router.params.name;
    if (keyword.value) {
        searchMeals()
    }
})
</script>