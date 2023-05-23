<script setup>
defineProps({
  text: {
    type: String
  }

})
</script>
<template>
    <footer class="footer">
        <div class="footer__wrapper">
            <div class="footer__text">
                 Copyright  &#169 2023 Gupta Hospital. All Rights reserved.| <p>Designed & developed by <b> Yamini Gupta </b></p>
            </div>
        </div>
    </footer>
</template>

<style lang="scss">
.footer {
    text-align: center;
    border-top: 1px solid black;
    padding: 1rem 0;
    color: wheat;
    font-size: small;
}
</style>