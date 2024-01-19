<script setup lang="ts">
import { onMounted } from "vue";
import Header from "@/components/modules/Header.vue";
import Footer from "@/components/modules/Footer.vue";
import Splash from "@/components/modules/Splash.vue"
import Home from "@/views/HomeView.vue";
import Skills from "@/views/SkillsView.vue";
import Works from "@/views/WorksView.vue";

onMounted(()=> {
  addIo('.fade-in', 'active');

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
    <Header />
    <Splash />
    <main class="main">
      <Home id="home" />
      <Skills class="fade-in" id="skills" />
      <Works class="fade-in" id="works" />
    </main>
    <Footer class="fade-in" />
</template>
