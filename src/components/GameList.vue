<script setup>
import {ref} from "vue";
import vinyl from "@/data/vinyl.json"
import Disc from "@/components/Disc.vue";

const vinylList = ref(vinyl)
const discPlayer = ref('Demon Days')
console.log(discPlayer.value)


</script>

<template>
    <div id="vinylList">
        <Disc v-for="vinyl in vinylList"
              @click="discPlayer = vinyl.title"
              :img="vinyl.img"
              :title="vinyl.title"
              :inside-color="vinyl.insideColor"
              :outside-color="vinyl.outsideColor"
              :disc-player="discPlayer"
              @selected-disc="(value) => discPlayer = value"
        />
    </div>
    <div id="vinylInfo">
        <div id="discPlayer"></div>
    </div>

</template>

<style scoped>
    #vinylList {
        display: flex;
        flex-wrap: wrap;
        width: 75%;
    }

    #vinylInfo {
        width: 25%;
    }

    #discPlayer {
        height: 300px;
        width: 350px;
        /*background-color: red;*/
    }

</style>