<script setup>
defineProps({
    src: {
    type: String,
    required: true
  },
    text: {
        type: String
    },
    link: {
        type: String,
        default: '/'
    },
    isHome: {
        type: Boolean,
        default: false
    },
    showSubtext: {
        type: Boolean,
        default: false
    },
    phoneNumbers: {
      type: Array
    }
})
</script>
<template>
  <div>
    <div class="header__image" :style="{backgroundImage:`linear-gradient(rgba(0, 0, 0, 0.527),rgba(0, 0, 0, 0.5)),url(${src})`}"/>
    <div class="header__text"> <NuxtLink :to="link">{{ text }} </NuxtLink></div>
    <div class="header__buttons" v-if="isHome">
      <NuxtLink to="/orthopaedy">
        <div class="header__buttons--main"> Orthopaedy</div> 
      </NuxtLink>
      <NuxtLink to="/gynaec">
        <div class="header__buttons--main"> Gynaecology</div>
      </NuxtLink>
    </div>

    <div class="header__subtitle" v-else-if="showSubtext">
      Serving with a smile
    </div>

    <div class="header__contact-info" v-else-if="phoneNumbers">
      <div class="header__contact-info--text">
        <span>
          To book appointment, call us at
        </span>
        <span v-for="number in phoneNumbers">
          <font-awesome-icon :icon="['fas', 'phone-flip']" />
          {{ number }}
        </span>
      </div>

    </div>

    <div v-else></div>
  </div>
</template>


<style lang="scss">
    .header {
        &__subtitle {
            @media screen and (max-width: 600px) {
                width: 100%;
            }
            font-size: x-large;
            position: absolute;
            top: 10rem;
            width: 50%;
            justify-content: center;
            display: flex;
            color: aliceblue;
        }

        &__image {
            height: 300px;
            width: 100%;
            background-size: cover;
            background-repeat: no-repeat;
        }

        &__contact-info {
            @media only screen and (max-width: 600px) {
                width: 100%;
            }

            position: absolute;
            top: 10rem;
            width: 50%;
            justify-content: center;
            color: white;
            display: flex;

            &--text {
                display: flex;
                flex-direction: column;
            }
        }

        &__text {
            @media only screen and (max-width: 600px) {
                width: 100%;
            }
            top: 4rem;
            z-index: 1;
            color: white;
            font-size: xxx-large;
            position: absolute;
            width: 50%;
            justify-content: center;
            display: flex;

        }
        &__buttons {
            @media only screen and (max-width: 600px) {
                width: 100%;
                z-index: 1;
            }
            display: flex;
            justify-content: space-evenly;
            top: 10rem;
            width: 50%;
            position: absolute;

            &--main {
                height: 50px;
                padding: 1rem 2rem;
                background-color: #f5f9e9;  
                color:  #093824;
                border: #093824 solid 2px;
                cursor: pointer;
                display: flex;
                align-items: center;
                justify-content: center;

                &:hover {
                    background-color: #093824;
                    color: #f5f9e9;
                    border: #f5f9e9 2px solid;
                }
            }
        }
    }
</style>