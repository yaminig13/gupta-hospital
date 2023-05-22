<script setup>
defineProps({
  contactInfo: {
    type: Object,
  }

})
</script>
<template>
    <div class="top-bar">
        <div class="top-bar__wrapper">
            <div class="top-bar__left"  v-if="contactInfo">
                <font-awesome-icon :icon="['fab', 'whatsapp']" />
                <span> {{ contactInfo.wa_no }} </span>
                <font-awesome-icon :icon="['fas', 'phone-flip']" />
                <span> {{ contactInfo.phs[0] }} </span>

            </div>
            <div v-else class="top-bar__title">
                <NuxtLink to="/">GUPTA HOSPITAL</NuxtLink>
            </div>
            <div class="top-bar__right">
                <NuxtLink to="/aboutus">
                    <div class="top-bar__right--item">
                        About Us
                    </div>
                </NuxtLink>
                <NuxtLink to="/contact">
                    <div class="top-bar__right--item">
                        Contact
                    </div>
                </NuxtLink>
                <NuxtLink to="/team">
                    <div class="top-bar__right--item">
                        Our Team
                    </div>
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
.top-bar{
    padding: 0.25rem 0 0.25rem 3rem;
    color: var(--color-lightest);
    width: 100%;
    background-color: var(--color-background);
    border: 1px solid var(--color-border);

    &__wrapper {
        @media only screen and (max-width: 600px) {
           justify-content: flex-end;
        }

        
        span {
            padding: 0 1rem 0 0;
        }
        display: flex;
        justify-content: space-between;
    }
    &__left {
        @media only screen and (max-width: 600px) {
           display: none;
        }
    }

    &__right {
        display: flex;

        a {
            border-right: 1px solid var(--color-lightest);
        }

        &--item {
            padding: 0 1rem;
            cursor: pointer;

            &:hover {
                background-color: var(--color-lightest);
                color: #093824;
            }
        }
    }
}
</style>