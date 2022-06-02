<template>
  <div id="app">
    <img
      class="davril_logo"
      alt="davril, immobilier durable"
      src="./assets/images/logo.png"
    />
    <img
      class="max_1366 hero"
      src="./assets/images/hero.png"
      alt="Pour habiter ou investir entre ville et nature."
    />
    <img
      class="max_1366 hero_mob"
      src="./assets/images/hero_mob.png"
      alt="Pour habiter ou investir entre ville et nature."
    />
    <GreyButton link="#form" text="Renseignez-vous vite&nbsp;!"></GreyButton>

    <Title
      id="forme_1"
      primaryTitle="Carré Nature :"
      secondaryTitle="une adresse unique à Saint-Brice-sous-Forêt&nbsp;!"
    ></Title>
    <p class="max_content_primary w90 my_2 description">
      Idéalement située au cœur d’une zone pavillonnaire, à quelques minutes à
      pied seulement du centre-ville et de ses services et commerces, la
      résidence Carré Nature bénéficie d’un cadre agréable.<br /><br />
      Carré Nature conserve volontairement une taille humaine, gage d’une
      qualité de vie appréciée. Ainsi, ce sont 19 appartements, lumineux et
      parfaitement agencés qui sont proposés.
    </p>

    <section class="location mt_1">
      <div class="plan max_content_primary w90">
        <img src="../src/assets/images/plan.png" alt="plan" />
        <article>
          <div>
            <h2 class="primary_title mb_4">Un emplacement de choix&nbsp;:</h2>
            <p>
              La situation géographique avantageuse de Saint-Brice-sous-Forêt,
              au coeur du Val d’Oise, ses accès rapides vers la capitale et son
              environnement vert en font un lieu de vie apprécié.
            </p>
          </div>
        </article>
      </div>
      <div class="flex_plan_wrapper max_content_secondary w90 mt_3 mb_1">
        <div>
          <div class="mb_1">
            <img src="./assets/images/visu_eiffel.svg" alt="tour eiffel" />
          </div>
          <p class="p_font20">
            À 12 km*
            <span> de Paris </span>
          </p>
        </div>
        <span></span>
        <div>
          <div class="mb_1">
            <img src="./assets/images/arbres.svg" alt="forêt" />
          </div>
          <p class="p_font20">
            À proximité de
            <span> la forêt de Montmorency </span>
          </p>
        </div>
        <span></span>
        <div>
          <div class="mb_1">
            <img src="./assets/images/visu_commerce.svg" alt="commerces" />
          </div>
          <p class="p_font20">
            Services et commerces à
            <span> quelques minutes* </span>
          </p>
        </div>
      </div>
      <div></div>
      <GreyButton link="#form" text="Prenez rendez-vous !"></GreyButton>
    </section>

    <section class="architecture">
      <div class="illustration max_1366 mb_4">
        <img
          src="./assets/images/ec1.jpg"
          alt="illustration intérieur d'appartement"
        />
        <div class="title_container">
          <Title
            primaryTitle="Une architecture élégante"
            secondaryTitle="et des prestations de qualité&nbsp;:"
          ></Title>
        </div>
      </div>
      <p class="max_content_primary w90">
        Dans cette résidence intimiste, l’architecture est à la fois classique
        et moderne et chaque appartement est pensé pour votre plus grand
        confort.
      </p>
      <div class="card_container max_content_secondary w90 mt_3 mb_1">
        <div class="card_wrapper">
          <div>
            <img src="./assets/images/visu_arbre.svg" alt="arbre" />
            <p class="p_font20">
              Espaces<br />
              végétalisés
            </p>
          </div>
          <div>
            <img src="./assets/images/visu_plan.svg" alt="plan" />
            <p class="p_font20">Du studio au <br />4 pièces</p>
          </div>
          <div>
            <img src="./assets/images/visu_velo.svg" alt="velo" />
            <p class="p_font20">
              Locaux<br />
              à vélos
            </p>
          </div>
        </div>
        <div class="card_wrapper">
          <div>
            <img src="./assets/images/visu_parking.svg" alt="parking" />
            <p class="p_font20">
              Parking en<br />
              sous-sol
            </p>
          </div>
          <div>
            <img src="./assets/images/visu_banc.svg" alt="banc" />
            <p class="p_font20">
              Résidence à<br />
              taille humaine
            </p>
          </div>
          <div>
            <img src="./assets/images/visu_balcon.svg" alt="balcon" />
            <p class="p_font20">Avec balcon ou <br />terrasse</p>
          </div>
        </div>
      </div>
      <GreyButton link="#form" text="En savoir plus, maintenant !"></GreyButton>
    </section>
    <ContactForm class="mt_1"></ContactForm>
    <footer class="mt_5 w90">
      <h2 class="primary_title">RENDEZ-VOUS PERSONNALISÉ AU</h2>
      <a class="secondary_title" href="tel:0800800889">0800 800 889</a>
      <p>Service et appel gratuits</p>
      <img
        class="davril_logo"
        alt="davril, immobilier durable"
        src="./assets/images/logo.png"
      />
    </footer>
  </div>
</template>

<script>
import Title from "./components/Title.vue";
import GreyButton from "./components/GreyButton.vue";
import ContactForm from "./components/ContactForm.vue";

export default {
  name: "App",
  components: {
    Title,
    GreyButton,
    ContactForm,
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

  input,
  select {
    font-family: "Open Sans", sans-serif;
  }

  .hero {
    @media #{$max480} {
      display: none;
    }
  }

  .hero_mob {
    display: none;
    @media #{$max480} {
      display: inherit;
    }
  }

  .davril_logo {
    width: clamp(7rem, 18vw, 13.5rem);
    margin: 1rem auto;
  }

  .description {
    margin-bottom: 9rem;
    position: relative;
    &::after {
      content: url(./assets/images/forme2.svg);
      z-index: -1;
      position: absolute;
      transform: translateX(-50%);
      left: 40%;
      top: -4rem;
      width: 45rem;
      height: auto;
      overflow: hidden;
    }

    @media #{$max768} {
      &::after {
        display: none;
      }
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
      display: flex;
      background-color: var(--white);
      position: relative;
      z-index: 2;

      & > article {
        width: 40%;
        display: flex;
        align-items: center;
        justify-content: center;

        & > div {
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

        & > article {
          width: 100%;
          margin: 1rem 0;

          & > div {
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

    .flex_plan_wrapper {
      display: flex;
      justify-content: space-between;
      align-items: center;

      & > span {
        display: block;
        width: 2px;
        height: 8rem;
        background-color: var(--primary_color);
      }

      & > div {
        width: 25%;
        max-width: 12rem;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        & > div {
          width: 4.8rem;
          height: 4.2rem;
          display: flex;
          justify-content: center;

          img {
            width: 100%;
            height: 100%;
            object-fit: contain;
          }
        }
        p {
          span {
            display: block;
            font-weight: var(--w600);
            color: var(--primary_color);
          }
        }
      }

      @media #{$max768} {
        flex-direction: column;

        & > span {
          height: 2px;
          width: 60%;
        }

        & > div {
          width: 80%;
          margin: 1rem 0;
          & > div {
            width: 3.5rem;
            height: 3.5rem;
            margin-bottom: 1rem;
          }

          p {
            span {
              display: inline;
            }
          }
        }
      }
    }
  }

  .architecture {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;

    .illustration {
      position: relative;

      .title_container {
        background-color: rgba(#ffffff, 0.9);
        max-width: 42rem;
        width: 80%;
        position: absolute;
        transform: translateX(-50%);
        left: 50%;
        bottom: 0;
        .title {
          padding-bottom: 0;
          h2 {
            margin-bottom: 0 !important;
            &::after {
              bottom: -1.5rem;
            }
          }
        }
      }
      @media #{$max480} {
        .title_container {
          width: 100%;
          position: inherit;
        }
      }
    }

    &::after {
      content: url(./assets/images/forme3.svg);
      position: absolute;
      transform: translateY(-50%);
      left: -11rem;
      top: 70%;
      width: 22rem;
      height: auto;
      overflow: hidden;

      @media #{$max768} {
        transform: translateY(-50%) scale(0.5);
      }
    }
    .card_container {
      .card_wrapper {
        width: 100%;
        display: flex;
        justify-content: space-between;

        & > div {
          margin: 0 1rem 2rem;
          padding: 1rem;
          max-width: 12.5rem;
          width: 100%;
          border: 2px solid var(--primary_color);
          display: flex;
          flex-direction: column;
          justify-content: flex-end;
          align-items: center;

          p {
            padding-top: 0.5rem;
            font-weight: var(--w600);
          }
        }
      }
    }

    @media #{$max768} {
      .card_container {
        .card_wrapper {
          flex-direction: column;
          align-items: center;
          & > div {
            margin: 0 0 1rem;
            padding: 0 0.5rem 0.5rem;
            max-width: 15rem;
            width: calc(70% - 2rem);
            img {
              transform: scale(0.6);
            }
            p {
              padding-top: 0;
            }
          }
        }
      }
    }
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

  footer {
    h2 {
      color: var(--primary_color);
    }
    a {
      color: var(--secondary_color);
      font-weight: var(--w600);
    }
    p {
      text-transform: uppercase;
      font-size: clamp(0.7rem, 1.5vw, 0.9rem);
      line-height: clamp(0.9rem, 2vw, 1.1rem);
      font-weight: var(--w600);
      color: var(--primary_color);
    }
  }
}
</style>
