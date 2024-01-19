<script setup lang="ts">
import Menu from "@/components/modules/Menu.vue"
</script>

<template>
    <footer class="footer">
        <img class="footer__bg1" src="@/assets/common/remoteControl.svg" alt="#">
        <div class="footer__inner">
            <div class="footer__bg2"></div>
            <div class="footer__container">
                <p class="eyctch--ending footer__ttl">finish</p>
                <nav class="nav footer__nav">
                    <Menu />
                </nav>
            </div>
        </div>
    </footer>
</template>