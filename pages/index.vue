<template>
  <main>
    <Announcement :text="announce.content"></Announcement>

    <Topbar :show-phone="true" :contact-info="contact"></Topbar>
    <Header :src="header.image" text="Gupta Hospital" :isHome="true"></Header>   

    <div class="home__highlights">

      <div class="home__highlights--item">
        <font-awesome-icon :icon="['fas', 'pills']" />
        <span>In-house Chemist</span>
      </div>
      <div class="home__highlights--item">
        <font-awesome-icon :icon="['far', 'clock']" />
        <span>Emergency Service 24 X 7</span>
      </div>
      <div class="home__highlights--item">
        <font-awesome-icon :icon="['fas', 'wallet']" />
        <span>Cashless payment</span>
      </div>
    </div>

    <div class="home__highlights company">
        <div class="home__highlights--title company"> Panel of Companies </div>

        <div class="home__highlights--wrapper company">
          <div class="home__highlights--item company"  v-for="company in companies" :style="{backgroundImage:`url(${company.cover}`}"></div>
        </div>
    </div>

    <Footer></Footer>
  </main>
</template>

<script>

export default {
    async asyncData({ $content }) {
        const companies = await $content("companies").fetch();
        const headers = await $content("header").fetch();
        const contacts = await $content("contact").fetch();
        const announces = await $content("announce").fetch();

        const header = headers[0];
        const contact = contacts[0];
        const announce = announces[0];
        return {
            companies,
            header,
            contact,
            announce
        };
    },
};
</script>

<style lang="scss">
.home {
  &__header--text {
    position: absolute;
    top: -10rem;
    width: 50%;
    text-align: center;
    color: white;
    display: flex;
    flex-direction: column;
  }

  &__highlights {
    @media only screen and (max-width: 600px) {
      align-items: center;
      justify-content: space-between;
      margin: 1rem;
      padding: 1rem;
    }
    background-color: var(--color-lightest);
    display: flex;
    margin: 4rem;
    padding: 2rem;
    justify-content: space-around;

    &.company {
      background-color: var(--color-lightest);
      display: block;
      margin: 4rem;
      padding: 2rem;

      @media only screen and (max-width: 600px) {
        margin: 2rem 1rem;
        padding: 1rem;
      }
    }

    &--title {
      text-align: center;
      font-size: xx-large;
    }

    &--wrapper {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
    }

    &--item {
      display: flex;
      flex-direction: column;
      // margin: 2rem;
      padding: 1rem;
      // background-color:  var(--color-background-light);
      height: 9rem;
      width: 9rem;
      justify-content: center;
      align-items: center;
      color: var(--color-background);
      text-align: center;

      svg {
        font-size: xx-large;
      }

      span {
        background-color: var(--vt-c-text-dark-2);        
        margin-top: 1rem;
        padding: .5rem;
      }

      &.company {
        @media only screen and (max-width: 600px) {
          height: 2.5rem;
          width: 5rem;
          margin: .5rem;
        }
        height: 5rem;
        width: 10rem;
        background-size: cover;
        background-repeat: no-repeat;
        margin: 2rem 1rem;
      }
    }
  }

  &__call {
    background-color: #093824;
    height: 3rem;
    color: #f5f9e9;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    border: 1px solid black;
  }
}
</style>
