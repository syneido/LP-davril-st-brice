<template>
  <div id="form">
    <Title
      class="my_3"
      primaryTitle="Contactez-nous dès maintenant pour en savoir plus"
      secondaryTitle=" et devenir propriétaire de votre appartement<br>
à Saint-Brice-sous-Forêt&nbsp;! "
    ></Title>
    <form @submit="onSubmit" class="max_content_secondary w90">
      <div class="flex_field">
        <input v-model="name" type="text" placeholder="Nom*" required />
        <input type="text" placeholder="Prénom*" required />
        <input type="text" placeholder="E-mail*" required />
        <input
          type="number"
          placeholder="Téléphone*"
          maxlength="8"
          pattern="[0-9]{8}"
          required
        />
        <input
          type="number"
          placeholder="Code postal*"
          maxlength="5"
          pattern="[0-9]{5}"
          required
        />
        <select name="lodging" id="lodging_select" required>
          <option value="" disabled selected>Type de logement recherché</option>
          <option value="1">Studio</option>
          <option value="2">Appartement 2 pièces</option>
          <option value="3">Appartement 3 pièces</option>
          <option value="4">Appartement 4 pièces</option>
        </select>
      </div>
      <p class="p_font20 my_2 budget_info">
        Pour un accompagnement sur-mesure, pourriez-vous nous indiquer votre
        budget&nbsp;?
      </p>
      <select class="mb_2" name="budget" id="budget_select" required>
        <option value="1">Entre 150 000€ et 250 000€</option>
        <option value="2">Entre 250 000 € et 350 000 €</option>
        <option value="3">Entre 350 000 € et 450 000 €</option>
      </select>
      <div class="flex_radio mt_2">
        <div>
          <input type="radio" id="huey" name="drone" value="huey" checked />
          <label for="huey">Oui</label>
        </div>

        <div>
          <input type="radio" id="dewey" name="drone" value="dewey" />
          <label for="dewey">Non</label>
        </div>
      </div>
      <p class="p_font20 condition my_2">
        Vous acceptez que vos données soient envoyées et traitées par DAVRIL en
        tant que responsable de traitement afin que nous puissions répondre à
        votre demande d’information sur le programme LES ALLÉES VICTORIA et vous
        contacter. Vos données sont conservées pendant 2 ans suivant votre
        dernière prise de contact. Vous pouvez exercer vos droits et vous
        désinscrire à tout moment. Pour en savoir plus, consultez notre
        politique de confidentialité.
      </p>
      <input type="submit" value="Je m’inscris" />
    </form>
  </div>
</template>

<script>
import Title from "./Title.vue";

export default {
  name: "ContactForm",
  components: {
    Title,
  },
  data() {
    return {
      firstName: "",
    };
  },
  methods: {
    async onSubmit(e) {
      e.preventDefault();
      
    //   const requestOptions = {
    //     method: "POST",
    //     headers: { "Content-Type": "application/json" },
    //     body: JSON.stringify({
    //       programIds: [640302757],
    //       MediaReference: 1867390035,
    //       isClaimedLead: false,
    //       needValidation: false,
    //       address: "1 rue de France",
    //       city: "Paris",
    //       postal_code: "75001",
    //       country: "AF",
    //       lastname: "La Taupe",
    //       firstname: this.name,
    //       company: "google",
    //       job: "Hunter",
    //       mobile_phone: "06123456789",
    //       landline_phone: "0123456789",
    //       job_phone: "0198765432",
    //       email: "rene.lataupe@mail.com",
    //       subject: "Achat région parisienne",
    //       message:
    //         "Bonjour, je serais intéressé par un bien en région parisienne.",
    //       nationality: "Française",
    //       origin: "Contact téléphonique",
    //       budget: "150000",
    //       civility: "M",
    //       nbRoomsDesired: [1],
    //       request_date: "2022-10-25 10:30",
    //       newsletterAccepted: true,
    //       custom_data: "{}",
    //       sellerEmail: "rene.lataupe@mail.com",
    //       osmArea: ["Paris"],
    //       commercialComment: "ceci est un commentaire",
    //       lotInformation: "Lot 6AB",
    //     }),
    //   };
    //   fetch(
    //     "https://test-davril.getunlatch.com/api/v1/lead-import/",
    //     requestOptions
    //   )
    //     .then(async (response) => {
    //       const data = await response.json();

    //       // check for error response
    //       if (!response.ok) {
    //         // get error message from body or default to response status
    //         const error = (data && data.message) || response.status;
    //         return Promise.reject(error);
    //       }

    //       this.postId = data.id;
    //     })
    //     .catch((error) => {
    //       this.errorMessage = error;
    //       console.error("There was an error!", error);
    //     });
    },
  },
};
</script>

<style scoped lang="scss">
@import "../assets/scss/variables";

#form {
  scroll-behavior: smooth;
  width: 100%;
  background-color: var(--background);
  display: flex;
  flex-direction: column;
  align-items: center;

  .budget_info {
    color: var(--primary_color);
  }

  .condition,
  label {
    font-size: clamp(0.7rem, 1.5vw, 0.9rem);
    line-height: clamp(0.9rem, 2vw, 1.1rem);
  }

  form {
    .flex_field {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: stretch;
      flex-wrap: wrap;
      gap: 2rem;
    }

    input,
    select {
      margin: 0 auto;
      -moz-box-sizing: border-box;
      -webkit-box-sizing: border-box;
      box-sizing: border-box;
      display: block;
      width: 15rem;
      max-width: 19rem;
      flex-grow: 1;
      flex-shrink: 1;
      font-size: 1rem;
      border: 1px solid var(--black);
      padding: 1rem;
      &:focus {
        outline: none !important;
      }
    }
    select {
      -webkit-appearance: none;
      -moz-appearance: none;
      background-color: var(--white) !important;
      background: url(../assets/images/caret.svg);
      background-position: center right 0.5rem;
      background-size: 1rem;
      background-repeat: no-repeat;
    }

    #budget_select {
      width: 17.5rem;
      margin: 0 auto;
    }

    .flex_radio {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 5%;
      & > div {
        display: flex;
        align-items: center;

        input {
          width: auto;
        }
        label {
          padding-left: 0.5rem;
          text-align: left;
        }
      }
    }
    input[type="submit"] {
      max-width: 22rem;
      width: 80%;
      transition: all 0.2s;
      display: block;
      margin-bottom: -1.7rem;
      padding: clamp(0.5rem, 2vw, 1rem) 0;
      background-color: var(--tertiary_color);
      color: var(--white);
      font-weight: var(--w600);
      font-size: clamp(1rem, 2vw, 1.2rem);
      border: 2px solid var(--tertiary_color);
      &:hover {
        background-color: var(--white);
        color: var(--tertiary_color);
      }
    }

    @media #{$max768} {
      .flex_field {
        gap: 1rem;
      }
      input,
      select {
        padding: 0.7rem;
      }
    }

    @media #{$max480} {
      #budget_select {
        width: 100%;
      }
      input[type="submit"] {
        margin-bottom: -1.1rem;
      }
    }
  }
}
</style>
