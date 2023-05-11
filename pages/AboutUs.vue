<template>
  <main>
    <Topbar :show-phone=true />
    <Header :src="about.image" text="Gupta Hospital" show-subtext=true></Header>
    <div class="about">

      <div class="about__title">
        About Us
      </div>

      <div class="about__text">
        {{ about.content }}
      </div>

    </div>
  </main>
</template>

<script>
export default {
   async asyncData({ $content }) {
    const abouts = await $content("about").fetch();
    const about=abouts[0]; 
    return {
      about,
    };
  },
};
</script>

<style lang="scss">
.about {
  padding-top: 2rem;
  background-color: #093824;

  &__title {
    color: #f5f9e9;
    font-size: xx-large;
    margin: 2rem;

  }

  &__text {
    color: #f5f9e9;
    font-size: medium;
    padding: 2rem;

  }
}
</style>
