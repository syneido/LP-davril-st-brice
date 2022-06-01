<template>
  <div id="form">
    <Title
      class="my_3"
      primaryTitle="Contactez-nous dès maintenant pour en savoir plus"
      secondaryTitle=" et devenir propriétaire de votre appartement<br>
à Saint-Brice-sous-Forêt&nbsp;! "
    ></Title>
    <ValidationObserver
      class="max_content_secondary w90"
      ref="observer"
      v-slot="{ invalid }"
    >
      <form @submit="onSubmit">
        <p class="error">{{ postError }}</p>
        <div class="flex_field">
          <ValidationProvider
            class="inputContainer"
            v-slot="{ errors }"
            rules="required"
            name="nom"
            mode="eager"
          >
            <input
              v-model="firstName"
              type="text"
              placeholder="Nom*"
              required
            />
            <span>{{ errors[0] }}</span>
          </ValidationProvider>

          <ValidationProvider
            class="inputContainer"
            v-slot="{ errors }"
            rules="required"
            name="prénom"
            mode="eager"
          >
            <input v-model="name" type="text" placeholder="Prénom*" required />
            <span>{{ errors[0] }}</span>
          </ValidationProvider>

          <ValidationProvider
            class="inputContainer"
            v-slot="{ errors }"
            rules="required|email"
            name="email"
            mode="eager"
            ><input
              v-model="email"
              type="text"
              placeholder="E-mail*"
              required
            />
            <span>{{ errors[0] }}</span></ValidationProvider
          >
          <ValidationProvider
            class="inputContainer"
            v-slot="{ errors }"
            rules="phone"
            name="téléphone"
            mode="eager"
            ><input
              v-model="tel"
              type="number"
              placeholder="Téléphone*"
              maxlength="10"
              pattern="[0-9]{10}"
              required
            /><span>{{ errors[0] }}</span></ValidationProvider
          >

          <ValidationProvider
            class="inputContainer"
            v-slot="{ errors }"
            rules="postalCodeRule"
            name="code postal"
            mode="eager"
          >
            <input
              v-model="postalCode"
              type="number"
              placeholder="Code postal*"
              maxlength="5"
              pattern="[0-9]{5}"
              required
            /><span>{{ errors[0] }}</span></ValidationProvider
          >
          <div class="inputContainer">
            <select
              v-model="roomNumber"
              name="lodging"
              id="lodging_select"
              required
            >
              <option value="" disabled selected>
                Type de logement recherché
              </option>
              <option value="1">Studio</option>
              <option value="2">Appartement 2 pièces</option>
              <option value="3">Appartement 3 pièces</option>
              <option value="4">Appartement 4 pièces</option>
            </select>
          </div>
        </div>
        <p class="p_font20 my_2 budget_info">
          Pour un accompagnement sur-mesure, pourriez-vous nous indiquer votre
          budget&nbsp;?
        </p>
        <div class="inputContainer" id="budget_select">
          <select v-model="budget" class="mb_2" name="budget" required>
            <option value="250000" selected>Entre 150 000€ et 250 000€</option>
            <option value="350000">Entre 250 000 € et 350 000 €</option>
            <option value="450000">Entre 350 000 € et 450 000 €</option>
          </select>
        </div>
        <div class="flex_radio mt_2">
          <div>
            <input
              v-model="ml"
              type="radio"
              id="oui"
              name="ml"
              value="oui"
              checked
            />
            <label for="oui">Oui</label>
          </div>

          <div>
            <input v-model="ml" type="radio" id="non" name="ml" value="non" />
            <label for="non">Non</label>
          </div>
        </div>
        <p class="p_font20 condition my_2">
          Vous acceptez que vos données soient envoyées et traitées par DAVRIL
          en tant que responsable de traitement afin que nous puissions répondre
          à votre demande d’information sur le programme LES ALLÉES VICTORIA et
          vous contacter. Vos données sont conservées pendant 2 ans suivant
          votre dernière prise de contact. Vous pouvez exercer vos droits et
          vous désinscrire à tout moment. Pour en savoir plus, consultez notre
          politique de confidentialité.
        </p>
        <input
          :disabled="ml === `non` || invalid ? true : false"
          type="submit"
          value="Je m’inscris"
        />
      </form>
    </ValidationObserver>
  </div>
</template>

<script>
import Title from "./Title.vue";
import {
  ValidationProvider,
  ValidationObserver,
  extend,
  localize,
} from "vee-validate";
import { required, email } from "vee-validate/dist/rules";
import fr from "vee-validate/dist/locale/fr.json";

extend("required", required);
extend("email", email);
extend("phone", (value) => {
  let regex = /^(0)[0-9](\d{1}){8}$/;
  if (!regex.test(value)) {
    return "Le téléphone est invalide";
  }
  return regex.test(value);
});
extend("postalCodeRule", (value) => {
  let regex = /^(([0-8][0-9])|(9[0-5]))[0-9]{3}$/;
  if (!regex.test(value)) {
    return "Le code postal est invalide";
  }
  return regex.test(value);
});

localize("fr", fr);

export default {
  name: "ContactForm",
  components: {
    Title,
    ValidationProvider,
    ValidationObserver,
  },
  data() {
    return {
      firstName: "",
      name: "",
      email: "",
      tel: "",
      postalCode: "",
      roomNumber: "",
      budget: 250000,
      ml: "oui",
      postError: "",
    };
  },
  methods: {
    async onSubmit(e) {
      e.preventDefault();
      if (this.ml != "oui") return;
      const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          programIds: [640302757],
          MediaReference: 1867390035,
          isClaimedLead: false,
          needValidation: false,
          address: "",
          city: "",
          postal_code: this.postalCode,
          country: "",
          lastname: this.name,
          firstname: this.firstName,
          company: "",
          job: "",
          mobile_phone: this.tel,
          landline_phone: "",
          job_phone: "",
          email: this.email,
          subject: "Contact Saint-Brice-Sous-Forêt",
          message: "",
          nationality: "",
          origin: "LP Carré Nature",
          budget: "150000",
          civility: "",
          nbRoomsDesired: [this.roomNumber],
          request_date: "",
          newsletterAccepted: true,
          custom_data: "{}",
          sellerEmail: "",
          osmArea: ["Lille"],
          commercialComment: "",
          lotInformation: "",
        }),
      };
      fetch(
        "https://test-davril.getunlatch.com/api/v1/lead-import/",
        requestOptions
      )
        .then(async (response) => {
          const data = await response.json();
          this.postError = "";

          // check for error response
          if (!response.ok) {
            // get error message from body or default to response status
            const error = (data && data.message) || response.status;
            return Promise.reject(error);
          }

          this.postId = data.id;
        })
        .catch((error) => {
          this.errorMessage = error;
          console.error("There was an error!", error);
          this.postError = "Une erreur est survenue";
        });
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
    position: relative;
    margin: 0 auto;

    .flex_field {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: stretch;
      flex-wrap: wrap;
      gap: 2rem;
    }

    .inputContainer > span,
    .error {
      color: red;
      font-size: 0.8rem;
      padding-top: 0.2rem;
    }

    .error {
      position: absolute;
      transform: translateX(-50%);
      left: 50%;
      top: -3rem;
    }

    .inputContainer {
      flex-grow: 1;
      flex-shrink: 1;
      width: 15rem;
      input,
      select {
        margin: 0 auto;
        width: 100%;
        height: 100%;
        -moz-box-sizing: border-box;
        -webkit-box-sizing: border-box;
        box-sizing: border-box;
        display: block;

        max-width: 19rem;

        font-size: 1rem;
        border: 1px solid var(--black);
        padding: 1rem;
        &:focus {
          outline: none !important;
        }
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
        input,
        label {
          cursor: pointer;
        }
        input {
          width: auto;
        }
        label {
          font-size: 0.9rem;
          padding-left: 0.5rem;
          text-align: left;
        }
      }
    }
    input[type="submit"] {
      cursor: pointer;
      margin: 0 auto;
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
      &:disabled {
        cursor: not-allowed;
        background-color: rgb(180, 180, 180);
        border-color: rgb(180, 180, 180);
        &:hover {
          background-color: rgb(180, 180, 180);
          color: var(--white);
        }
      }
    }

    @media #{$max768} {
      #budget_select {
        width: 100%;
      }
      .flex_field {
        gap: 1rem;
      }
      input,
      select {
        padding: 0.7rem;
      }
    }

    @media #{$max480} {
      input[type="submit"] {
        margin-bottom: -1.1rem;
      }
    }
  }
}
</style>
