<script setup lang="ts">
import ftprntImg from "@/assets/common/footprint.svg";
import { onMounted } from "vue";
import { addIo } from "@/components/modules/Functions.vue"

onMounted(() => {
    addIo('.ftprnts__img', 'appear');
});


</script>
<template>
    <div class="ftprnts">
        <img v-for="i in 8" :key=i :src=ftprntImg alt="#" class="ftprnts__img">
    </div>
</template>