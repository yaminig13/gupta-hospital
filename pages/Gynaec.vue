<template>
  <main>
    <Topbar></Topbar>
    <Header :src="gynaec.image" :text="gynaec.title" buttons="false" :phone-numbers="gynaec.phs" link="/gynaec"></Header>
    <div class="ortho">
      <div class="ortho__highlights service">

        <div class="ortho__highlights--title service"> Services </div>

        <div class="ortho__highlights--wrapper service">
          <div class="ortho__highlights--item service" v-for="service in gynaec.services">
            <i class="fa-solid fa-x-ray"></i>
            <span> {{ service }} </span>
          </div>
        </div>
      </div>

      <div class="ortho__highlights surgery">
        <div class="ortho__highlights--title surgery"> Surgeries </div>

        <div class="ortho__highlights--wrapper surgery">
          <div class="ortho__highlights--item surgery" v-for="surgery in gynaec.surgeries">
            <span> {{ surgery }} </span>
          </div>
        </div>
      </div>
    </div>
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
};
</script>

<style lang="scss">

.ortho {
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
      display: flex;
      justify-content: center;
    }

    &--item {
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
        height: 10rem;
        width: 15rem;
      }

      &.surgery {
        background-color: var(--color-background);
        color: #f5f9e9;
        height: 5rem;
        width: 10rem;
      }
      svg {
        font-size: xx-large;
        padding-bottom: 1rem;
      }
    }
  }
}
</style>
