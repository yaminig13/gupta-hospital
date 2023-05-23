<template>
  <main>
    <Topbar></Topbar>
    <Header :src="gynaec.image" :text="gynaec.title" buttons="false" :phone-numbers="gynaec.phs" link="/gynaec"></Header>
    <div class="gynaec">
      <div class="gynaec__highlights service">

        <div class="gynaec__highlights--title service"> Services </div>

        <div class="gynaec__highlights--wrapper service">
          <div class="gynaec__highlights--item service" v-for="service in gynaec.services">
            <i class="fa-solid fa-x-ray"></i>
            <span> {{ service }} </span>
          </div>
        </div>
      </div>

      <div class="gynaec__highlights surgery">
        <div class="gynaec__highlights--title surgery"> Surgeries </div>

        <div class="gynaec__highlights--wrapper surgery">
          <div class="gynaec__highlights--item surgery" v-for="surgery in gynaec.surgeries" @click="toggleDesc(surgery)">
            <span> {{ surgery.name }} </span>
          </div>
        </div>
        <div class="gynaec__highlights--desc" v-show="description">
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
    const gynaecs = await $content("gynaec").fetch();
    const gynaec=gynaecs[0]; 
    return {
      gynaec,
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
      setTimeout(document.querySelector('.gynaec__highlights .surgery').scrollIntoView(),300);
    }
  }
};
</script>

<style lang="scss">

.gynaec {
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
    
    &.surgery {
      background-color: var(--color-lightest);
    }

    &--info {
      font-size: x-small;
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
