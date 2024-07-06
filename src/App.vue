<script setup>
import VinylList from "@/components/VinylList.vue";
import VinylTable from "@/components/VinylTable.vue";
import Spotify from "@/components/Spotify.vue";
import {ref} from "vue";

const selectedVinyl = ref(null)
console.log(selectedVinyl.value)

</script>

<template>
    <VinylList :selected-vinyl="selectedVinyl" />
    <Spotify v-if="selectedVinyl !== null" />
    <VinylTable v-else />
</template>

<style scoped>

</style>
