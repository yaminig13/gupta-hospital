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
          <div class="ortho__highlights--item surgery" v-for="surgery in ortho.surgeries">
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
    const orthos = await $content("ortho").fetch();
    const ortho = orthos[0];
    return {
      ortho,
    };
  },
};
</script>

<style lang="scss">

.ortho {
  &__highlights {

    display: flex;
    padding: 2rem;
    justify-content: space-between;
    flex-direction: column;
    
    &.service {
      font-size: large;
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
        flex-direction: column;
        align-items: center;
      }

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
      text-align: center;

      &.service {
        background-color: #f5f9e9;
        color: #093824;
        height: 10rem;
        width: 15rem;
      }

      &.surgery {
        background-color: #093824;
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
