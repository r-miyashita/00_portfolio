<script setup lang="ts">
import ftprntImg from "@/assets/common/footprint.svg";
import { onMounted } from "vue";

onMounted(() => {
    addIo('.ftprnts__img', 'appear');
    function addIo(target: string, key: string): void {
        const els = document.querySelectorAll(target);
        const addition = key;
        const addClass = (entries: any): void => {
            entries.forEach( (entry: any) => {
                if(entry.isIntersecting && !entry.target.classList.contains(addition)) {
                    entry.target.classList.add(addition);
                }
            });
        }; 
        const io = new IntersectionObserver(addClass);
        els.forEach(el => {
            io.observe(el);
        });
    }
});


</script>
<template>
    <div class="ftprnts">
        <img v-for="i in 8" :key=i :src=ftprntImg alt="#" class="ftprnts__img">
    </div>
</template>