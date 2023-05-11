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
    background-color: #093824;
    padding-top: 5px;

    &__wrapper {
        @media only screen and (max-width: 600px) {
           justify-content: flex-end;
        }

        span {
            padding: 0 1rem 0 0;
        }

        padding: 0 0 0 3rem;
        color: #f5f9e9;
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

        &--item {
            padding: 0 1rem;
            border-right: 1px solid white;
            cursor: pointer;

            &:hover {
                background-color: #f5f9e9;
                color: #093824;
            }
        }
    }
}
</style>