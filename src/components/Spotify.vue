<script setup>
import {ref} from "vue";
import vinyl from "@/data/vinyl.json"

defineProps({
    title:String,
})

const vinylList = ref(vinyl)


</script>

<template>
    <div>
        <iframe
            :src="vinylList[0].spotify"
            width="100%" height="100%" frameBorder="0" allowFullScreen=""
            allow="autoplay; clipboard-write encrypted-media; fullscreen; picture-in-picture"
            loading="lazy">
        </iframe>
    </div>
</template>

<style scoped>

</style>