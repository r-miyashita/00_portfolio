<script setup lang="ts">
import Ftprnts from "@/components/modules/Ftprnts.vue";
import mvImg from "@/assets/home/mv.svg";
import drImg from "@/assets/home/door.svg";
import { onMounted } from "vue";

function addClass(entries: any): void {
    entries.forEach( (entry: any) => {
        if(entry.isIntersecting && !entry.target.classList.contains('open')) {
            entry.target.classList.add('open');
        }
    });
}

onMounted(() => {
    const els = document.querySelectorAll('.door');
    const options = {rootMargin: "-20% 0px"};
    const io = new IntersectionObserver(addClass, options);
    els.forEach(el => {
        io.observe(el);
    })
});
</script>

<template>
    <section class="home">
        <div class="container home__container">
            <img :src=mvImg alt="mainvisual" class="home__mv">
            <div class="intrdcton home__intrdcton">
                <h2 class="ttl intrdcton__ttl">Introduction</h2>
                <p class="txt--wider intrdcton__txt">
                    1991年、鹿児島生まれ。
                    <br>2019年に福岡へ移住しエンジニアとしての活動を開始。
                    <br>これまでのメインキャリアとなるDB開発からWEB系へ転身を遂げるべく自己研鑽の日々を過ごす。
                    <br>現在は”Front-end” 学習中。
                </p>
            </div>
        </div>
        <img class="door" :src=drImg alt="#">
        <Ftprnts />
    </section>
</template>
