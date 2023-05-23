<template>
  <main>
    <Topbar></Topbar>
    <!-- <Header src="/src/assets/heading.jpg" text="Gupta Hospital"></Header> -->
    <div class="team__title">
        Our Surgeons
    </div>

    <div class="team__pictures">
        <div class="team__pictures--doc1" :style="{backgroundImage:`linear-gradient(rgba(0, 0, 0, 0.527),rgba(0, 0, 0, 0.5)),url(${team.img_pa})`}">
            <div class="team__pictures--info">
                <span class="large">Dr. Pratibha Gupta</span>
                <span v-for="info in team.info_pr">{{ info }}</span>
            </div>
        </div>
        <div class="team__pictures--doc2" :style="{backgroundImage:`linear-gradient(rgba(0, 0, 0, 0.527),rgba(0, 0, 0, 0.5)),url(${team.img_pr})`}">
            <div class="team__pictures--info">
                <span class="large">Dr. Padam Gupta</span>
                <span v-for="info in team.info_pa">{{ info }}</span>
            </div>
        </div>
    </div>

    <div class="team__title">
        Our Team
    </div>
    <div class="team__pictures">
        <div class="team__pictures--team" :style="{backgroundImage:`linear-gradient(rgba(0, 0, 0, 0.527),rgba(0, 0, 0, 0.5)),url(${team.img_team})`}">
            <div class="team__pictures--info">
                <span v-for="info in team.info_team">{{ info }}</span>
            </div>
        </div>
    </div>
    <Footer></Footer>

  </main>
</template>

<script>
export default {
   async asyncData({ $content }) {
    const teams = await $content("team").fetch();
    const team = teams[0]; 
    return {
      team,
    };
  },
};
</script>

<style lang="scss">
.team {
    &__title {
        justify-content: center;
        display: flex;
        font-size: x-large;
        color: white;
    }

    &__pictures {
        @media only screen and (max-width: 600px) {
            flex-direction: column;
        }

        display: flex;
        &--doc1, &--doc2 {
            @media only screen and (max-width: 600px) {
                width: 100%
            }
            height: 20rem;
            width: 50%;
            background-size: cover;
            background-repeat: no-repeat;
        }

        &--team {
            // background-image: linear-gradient(rgba(0, 0, 0, 0.527),rgba(0, 0, 0, 0.5)),url('../assets/team.jpg');;
            height: 20rem;
            width: 100%;
            background-size: cover;
            background-repeat: no-repeat;
        }

        // &--doc1 {
        //     background-image: linear-gradient(rgba(0, 0, 0, 0.527),rgba(0, 0, 0, 0.5)),url('../assets/doctor1.jpg');
        // }

        // &--doc2 {
        //     background-image: linear-gradient(rgba(0, 0, 0, 0.527),rgba(0, 0, 0, 0.5)),url('../assets/doctor2.jpg');
        // }

        &--info {
            padding: 2rem;
            color: aliceblue;
            display: flex;
            flex-direction: column;
        }
    }
}
</style>
