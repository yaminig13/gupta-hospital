<script setup>
// import Header from '../components/Header.vue'
// import TopBar from '../components/TopBar.vue';

let companies=[
  {
    name:'ongc',
    src:'/src/assets/ongc.png'
  },
  {
    name:'ongc',
    src:'/src/assets/ongc.png'
  }
];
</script>

<template>
  <main>
    <Topbar show-phone="true"></Topbar>
    <Header src="/src/assets/heading.jpg" text="Gupta Hospital" isHome="true"></Header>   

    <div class="home__highlights">

      <div class="home__highlights--item">
        <i class="fa-solid fa-pills"></i>
        <span>In-house Chemist</span>
      </div>
      <div class="home__highlights--item">
        <i class="fa-regular fa-clock"></i>
        <span>Emergency Service 24 X 7</span>
      </div>
      <div class="home__highlights--item">
        <i class="fa-solid fa-wallet"></i>
        <span>Cashless payment</span>
      </div>
    </div>

    <div class="home__highlights company">
        <div class="home__highlights--title company"> Panel of Companies </div>

        <div class="home__highlights--wrapper company">
          <div class="home__highlights--item company"  v-for="company in companies" :style="{backgroundImage:`url(${company.src})`}"></div>
        </div>
      </div>
  </main>
</template>

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
      flex-direction: column;
      align-items: center;
    }

    background-color: #093824;
    display: flex;
    // margin: 2rem;
    padding: 2rem;
    justify-content: space-between;

    &.company {
      background-color: #f5f9e9;
      display: block;
    }

    &--title {
      text-align: center;
      font-size: xx-large;
      margin-top: 2rem;
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
      background-color:  #f5f9e9;
      color: #093824;
      height: 10rem;
      width: 15rem;
      justify-content: center;
      align-items: center;

      svg {
        font-size: xx-large;
      }

      span {
        margin-top: 1rem;
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
