<script setup lang="ts">
import { onMounted } from "vue";
import { addIo } from "@/components/modules/Functions.vue"
import Header from "@/components/modules/Header.vue";
import Footer from "@/components/modules/Footer.vue";
import Splash from "@/components/modules/Splash.vue"
import Home from "@/views/HomeView.vue";
import Skills from "@/views/SkillsView.vue";
import Works from "@/views/WorksView.vue";

onMounted(()=> {
  addIo('.fade-in', 'active');
});

</script>

<template>
    <Header />
    <Splash />
    <main class="main">
      <Home id="home" />
      <Skills class="fade-in" id="skills" />
      <Works class="fade-in" id="works" />
    </main>
    <Footer class="fade-in" />
</template>
