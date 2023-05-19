<template>
  <main>
    <Announcement :text="announce.content"></Announcement>
    <Topbar :show-phone=true></Topbar>
    <Header :src="contact.image" text="Gupta Hospital" :show-subtext=true></Header>
    <div class="contact">
        <div class="contact__address">
            <a href="https://goo.gl/maps/5R9Y6re4KRzjGVAy6?coh=178572&entry=tt">
                <font-awesome-icon :icon="['fas', 'location-dot']" /></a>
                <span v-for="line in contact.address">{{ line }}</span>
            
        </div>
        <div class="contact__timings">
            <span class="contact__title">Visiting hours</span>
            <div class="contact__timings--wrapper">
                <div class="contact__timings--item">
                    <div class="contact__timings--item-title">Dr. Pratibha Gupta</div>
                    <div v-for="timing in contact.timings_pr">{{ timing }}</div>
                </div>
                <div class="contact__timings--item">
                    <div class="contact__timings--item-title">Dr. Padam Gupta</div>
                    <div v-for="timing in contact.timings_pa">{{ timing }}</div>

                </div>
            </div>
        </div>

        <div class="contact__booking">
            <span>
                To book appointment, call us at
            </span>
            <span v-for="ph in contact.phs">
                <font-awesome-icon :icon="['fas', 'phone-flip']" />
                {{ph}}
            </span>
        </div>

        <div class="contact__note">
            <span>We are open 24X7 in case of emergencies</span>
        </div>
    </div>
  </main>
</template>

<script>
export default {
   async asyncData({ $content }) {
    const contacts = await $content("contact").fetch();
    const contact = contacts[0]; 
    const announces = await $content("announce").fetch();
    const announce = announces[0];

    return {
      contact,announce
    };
  },
};
</script>

<style lang="scss">
.contact {
    @media only screen and (max-width: 600px) {
        grid-template-columns: unset;
        grid-template-rows: 1fr 2fr 1fr;
    }
    color: #f5f9e9;
    padding: 2rem;
    font-size: medium;
    display: grid;
    grid-template-columns: 2fr 2fr;
    grid-template-rows: 1fr 1fr;

    &__title {
        padding: 2rem 0;
        text-decoration: underline;
    }

    &__address {
        @media only screen and (max-width: 600px) {
            border-bottom: 1px solid;
        }
        display: flex;
        flex-direction: column;
        margin: 2rem;

        svg {
            position: absolute;
            top: -2rem;
        }
    }

    &__timings {
        @media only screen and (max-width: 600px) {
            margin: 1rem 2rem;
            border-bottom: 1px solid;
            padding: 1rem 0;
        }
        &--wrapper {
            @media only screen and (max-width: 600px) {
                flex-direction: column;
            }
            display: flex;
        }

        &--item {
            padding: 2rem 4rem 0 0rem;
        }

        &--item-title {
            padding-bottom: 2rem;
        }
    }

    &__booking {
        display: flex;
        padding: 2rem;
        flex-direction: column;
    }

    &__note {
       padding: 2rem; 
    }
}
</style>
