<script setup>
defineProps({
  text: {
    type: String,
    required: true
  }

})
</script>
<template>
    <div class="announce-bar" v-if="text">
        <div class="announce-bar__wrapper">
            <div class="announce-bar__text">
                {{ text }}
            </div>
        </div>
    </div>
</template>

<style lang="scss">
.announce-bar{
    background-color: var(--color-announcement);
    padding-top: 5px;
    color: aliceblue;
    display: flex;
    justify-content: center;
    padding: 0 .5rem;
}
</style>