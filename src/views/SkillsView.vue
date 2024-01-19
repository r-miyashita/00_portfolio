<script setup lang="ts">
import Ftprnts from "@/components/modules/Ftprnts.vue";
import mkupImg from "@/assets/skills/pictureFrameMkUp.svg";
import mkupIco from "@/assets/skills/icons/icSetMkUp.svg";
import fredImg from "@/assets/skills/pictureFrameFrEd.svg";
import fredIco from "@/assets/skills/icons/icSetFrEd.svg"; 
import bkedImg from "@/assets/skills/pictureFrameBkEd.svg";
import bkedIco from "@/assets/skills/icons/icSetBkEd.svg";
import { ref } from "vue";

const activeTab = ref("Markup"); // タブの選択状態とコンテンツ表示内容を判定するキーワード

const tabs = ["Markup", "Front-end", "Back-end"] // タブの選択肢

const skillMap = new Map([ // タブに対応するコンテンツ
  ["Markup",{
    img: mkupImg,
    ico: mkupIco,
    txt: "命名規則(BEM)を用いて、簡単なWeb制作が可能です。<br>DartSassで効率性やメンテナンス性など考慮しながら作業に取り組んでいます。"
  }],
  ["Front-end",{
    img: fredImg,
    ico: fredIco,
    txt: "現在、Vue3を学習中です。リアクティブ機能やリストレンダリングを使った単純な静的サイトの制作は可能です。<br>ストアやデータバインディングなど、その他主要となる機能への理解を深めるために今後はアプリ作成に挑戦していく予定です。"
  }],
  ["Back-end",{
    img: bkedImg,
    ico: bkedIco,
    txt: "phpはLaravel(MySQL)を使ってCRUD機能の実装を行った経験があります。<br>SQLは性能改善やIF追加に伴う改修など、案件担当として基本設計~リリースの工程に携わった経験があります。"
  }]
]);

</script>

<template>
    <section class="skills">
        <div class="container skills__container">
            <h2 class="ttl skills__ttl">Skills</h2>
            <ul class="skills__btn-list">
                <li class="button skills__btn"
                    v-for="(tab, index) in tabs"
                    :key=index
                    :class="{active: activeTab === tab}"
                    @click="activeTab = tab">
                    {{ tab }}
                </li>
            </ul>
            <div class="skill skills__content">
                <div class="skill__mv">
                    <img class="skill__img" :src="skillMap.get(activeTab)?.img" alt="#">
                </div>
                <div class="skill__dscrpton">
                    <img :src="skillMap.get(activeTab)?.ico" alt="#">
                    <p class="txt" v-html="skillMap.get(activeTab)?.txt"></p>
                </div>
            </div>
        </div>
        <div class="skills__bg"></div>
        <Ftprnts />
    </section>
</template>