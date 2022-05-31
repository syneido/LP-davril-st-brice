<template>
  <div id="app">
    <img class="davril_logo" alt="davril, immobilier durable" src="./assets/images/logo.png" />
    <img class="max_1366" src="./assets/images/hero.png" alt="Pour habiter ou investir entre ville et nature." />
    <GreyButton link="#" text="Renseignez-vous vite&nbsp;!"></GreyButton>

    <Title id="forme_1" primaryTitle="Carré Nature :"
      secondaryTitle="une adresse unique à Saint-Brice-sous-Forêt&nbsp;!"></Title>
    <p class="max_content_primary w90 my_2 description" v-html="description"></p>

    <section class="location my_1">
      <div class="plan max_content_primary w90">
        <img src="../src/assets/images/plan.png" alt="plan" />
        <article>
          <div>
            <h2 class="primary_title mb_4">Un emplacement
              de choix&nbsp;: </h2>
            <p v-html="planInfo"></p>
          </div>
        </article>
      </div>
    </section>

    <div class="form">
      <Title class="my_3" primaryTitle="Contactez-nous dès maintenant pour en savoir plus" secondaryTitle=" et devenir propriétaire de votre appartement
à Saint-Brice-sous-Forêt&nbsp;! "></Title>
    </div>
  </div>
</template>

<script>
import Title from "./components/Title.vue";
import GreyButton from "./components/GreyButton.vue";

export default {
  name: "App",
  components: {
    Title,
    GreyButton,
  },
  data() {
    return {
      description:
        "Idéalement située au cœur d’une zone pavillonnaire, à quelques minutes à pied seulement du centre-ville et de ses services et commerces, la résidence Carré Nature bénéficie d’un cadre agréable.<br><br> Carré Nature conserve volontairement une taille humaine, gage d’une qualité de vie appréciée. Ainsi, ce sont 19 appartements, lumineux et parfaitement agencés qui sont proposés.",
      planInfo: "La situation géographique avantageuse de Saint-Brice-sous-Forêt, au coeur du Val d’Oise, ses accès rapides vers la capitale et son environnement vert en font un lieu de vie apprécié.",

    };
  },
};
</script>

<style lang="scss">
@import "../src/assets/scss/variables";
@import "../src/assets/scss/main";

* {
  margin: 0;
  padding: 0;
}

#app {
  margin: 0 auto;
  font-family: "Open Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow-x: hidden;

  .davril_logo {
    width: clamp(7rem, 18vw, 13.5rem);
    margin: 1rem 0;
  }

  .description {
    margin-bottom: 9rem;
    @media #{$max768}{
      margin-bottom: 7rem;
    }
  }

  .location {
    width: 100%;
    background-color: var(--background);
    display: flex;
    flex-direction: column;
    align-items: center;

    .plan {
      margin-top: -5rem;
      padding-top: -5rem;
      display: flex;
      background-color: var(--white);

      &::after {
        content: url(./assets/images/forme2.svg);
        position: absolute;
        transform: translateX(-50%);
        right: 50%;
        top: 0;
        width: 19rem;
        height: auto;
        overflow: hidden;

        @media #{$max768} {
          transform: translateY(-50%) scale(0.5);
        }
      }

      &>article {
        display: flex;
        align-items: center;
        justify-content: center;

        &>div {
          width: 87%;

          p,
          h2 {
            text-align: left;
          }

          h2 {
            color: var(--primary_color);
            position: relative;

            &:after {
              position: absolute;
              display: block;
              content: "";
              border-bottom: 2px solid var(--primary_color);
              left: 0;
              right: 0;
              bottom: -2rem;
            }
          }
        }
      }

      img {
        width: 60%;
      }


    }

    @media #{$max768} {
      .plan {
        img {
          width: 100%;
        }

        &>article {
          margin: 1rem 0;

          &>div {
            h2 {
              margin-bottom: 2rem;

              &::after {
                bottom: -1rem;
              }
            }
          }
        }

        flex-direction: column;
      }
    }
  }

  .form {
    width: 100%;
    background-color: var(--background);
  }

  #forme_1 {
    position: relative;

    &::after {
      content: url(./assets/images/forme1.svg);
      position: absolute;
      transform: translateY(-50%);
      right: -10rem;
      top: 50%;
      width: 19rem;
      height: auto;
      overflow: hidden;

      @media #{$max768} {
        transform: translateY(-50%) scale(0.5);
      }
    }
  }
}
</style>
