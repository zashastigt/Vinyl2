<script setup>

    import {ref} from "vue";

    defineProps({
        title:String,
        img:String,
        insideColor:String,
        outsideColor:String,
        discPlayer:String
    })

    const emit = defineEmits(['selectedDisc'])
    console.log(emit)
    const isMobile = ref(true)

    function setSelectedDisc(value) {
        console.log(value)
        emit('selectedDisc', value)
    }

</script>

<template>
    <div id="album" @click="setSelectedDisc(title)">
        <img alt="album art" :src="'src/assets/albumArt/' + img">
        <div id="disc">
            <div id="discInside">
                <img alt="album art" :src="'src/assets/albumArt/' + img">
            </div>
        </div>
    </div>

</template>

<style scoped>

    #album {
        position: relative;
        height: 200px;
        width: 200px;
        margin: 10px;
    }

    #album img {
        height: 100%;
        width: 100%;
    }

    #disc {
        position: absolute;
        top: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-shrink: 0;
        height: 200px;
        width: 200px;
        border-radius: 50%;
        background-color: v-bind(outsideColor);
        z-index: -1;
    }

    #album:hover #disc {
        animation-name: hoverAlbum;
        animation-duration: 1s;
        animation-fill-mode: forwards;
        z-index: 1;
    }

    #album:hover img {
        transform: scale(1.1);
        z-index: 2;
    }

    #discInside {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 45%;
        width: 45%;
        border-radius: 50%;
        background-color: v-bind(insideColor);
        overflow: hidden;
    }

    #disc img {
        height: 90%;
        width: 90%;
        border-radius: 50%;
    }

    @keyframes hoverAlbum {
        0% {
            transform: translateX(0) rotate(0) scale(1);
        }

        100% {
            transform: translateX(100px) rotate(360deg) scale(1.1);
        }
    }

    @keyframes selectDisc {
        0% {
            transform: translateX(0) rotate(0);
            opacity: 1;
        }

        50% {
            opacity: 1;
        }

        100% {
            transform: translateX(200px) rotate(360deg);
            opacity: 0;
        }
    }
</style>