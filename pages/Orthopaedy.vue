<template>
  <main>
    
    <Topbar></Topbar>
    <Header :src="ortho.image" :text="ortho.title" link="/orthopaedy" :phone-numbers="ortho.phs"></Header>
    <div class="ortho">

      <div class="ortho__highlights service">
        <div class="ortho__highlights--title service"> Services </div>
        <div class="ortho__highlights--wrapper service">
          <div class="ortho__highlights--item service" v-for="service in ortho.services">
            <i class="fa-solid fa-x-ray"></i>
            <span> {{ service }} </span>
          </div>
        </div>
      </div>

      <div class="ortho__highlights surgery">
        <div class="ortho__highlights--title surgery"> Surgeries </div>

        <div class="ortho__highlights--wrapper surgery">
          <div class="ortho__highlights--item surgery" v-for="surgery in ortho.surgeries" @click="toggleDesc(surgery)">
            <span> {{ surgery.name }} </span>
          </div>
        </div>
        <div class="ortho__highlights--desc" v-show="description">
          <div class="info surgery"> {{ description }} </div>
        </div>
      </div>
    </div>
    <Footer></Footer>

  </main>
</template>

<script>
export default {
   async asyncData({ $content }) {
    const orthos = await $content("ortho").fetch();
    const ortho = orthos[0];
    return {
      ortho,
    };
  },

  data() {
    return {
      description: null,
    }
  },
  methods: {
    toggleDesc(surgery) {
      this.description = surgery.desc;
      setTimeout(document.querySelector('.ortho__highlights .surgery').scrollIntoView(),300);
    }
  }
};
</script>

<style lang="scss">

.ortho {
  &__highlights {

    display: flex;
    padding: 2rem;
    justify-content: space-between;
    flex-direction: column;

    &--desc {
      margin: .5rem;
      color: white;

      .info {
        padding: 1rem;

        &.surgery {
          background: var(--color-background);
        }
      }
    }
    
    
    &.service {
      font-size: large;
    }

    &.surgery {
      background-color: var(--color-lightest);
    }

    &--title {
      text-align: center;
      font-size: xx-large;

      &.service {
        color: #f5f9e9;
      }
    }


    &--wrapper {
      @media only screen and (max-width: 600px) {
        align-items: center;
      }

      display: flex;
      justify-content: center;
      flex-wrap: wrap;
    }

    &--item {
      @media only screen and (max-width: 600px) {
        padding: 1rem;
        margin: .5rem;
        flex: 1;
      }
      display: flex;
      flex-direction: column;
      border: 2px solid black;
      margin: 2rem;
      padding: 2rem;
      justify-content: center;
      align-items: center;
      text-align: center;

      &.service {
        background-color: var(--color-lightest);
        color: var(--color-border);
        height: 5rem;
        width: 15rem;
      }

      &.surgery {
        cursor: pointer;
        background-color: var(--color-background);
        color: #f5f9e9;
        height: 5rem;
        width: 10rem;
        border-radius: 1rem;

        &:focus {
          background-color: var(--color-background-light);
        }
      }

      svg {
        font-size: xx-large;
        padding-bottom: 1rem;
      }
    }
  }
}
</style>
