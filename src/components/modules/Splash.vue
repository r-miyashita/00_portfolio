<script setup lang="ts">
import { ref, onMounted } from 'vue';
const isVisited = ref(true);
const text = "welcome  to  myPortfolio";

onMounted(() => {
    if(!sessionStorage.getItem("visited")) {
        isVisited.value = false;
        setTimeout(() => {
            sessionStorage.setItem("visited", "first");
            isVisited.value = true;
        }, 3500);
    }
});
</script>

<template>
    <Transition>
        <div class="splash" v-if="!isVisited">
            <span class="splash__item"
                v-for="(t, index) in text"
                :key="index"
                v-text="t"
            />
        </div>
    </Transition>
</template>

<style scoped>
.v-leave-active {
    transition: opacity .75s ease;
}

.v-leave-to {
    opacity: 0;
}
</style>