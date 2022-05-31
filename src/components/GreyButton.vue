<template>
  <div class="mx_1 my_2">
    <a :href="link" target="_blank" v-html="text"></a>
  </div>
</template>

<script>
export default {
  name: "GreyButton",
  props: {
    text: String,
    link: String,
  },
};
</script>

<style scoped lang="scss">
div {
  max-width: 22rem;
  width: 80%;


  a {
    transition: all 0.2s;
    display: block;
    padding: clamp(0.5rem, 2vw, 1rem) 0;
    background-color: var(--tertiary_color);
    color: var(--white);
    font-weight: var(--w600);
    font-size: clamp(1rem, 2vw, 1.2rem);
    border: 2px solid var(--tertiary_color);
    &:hover{
      background-color: var(--white);
      color: var(--tertiary_color);
    }
  }
}
</style>
