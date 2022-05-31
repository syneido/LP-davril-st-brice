<template>
  <div class="title">
    <p class="primary_title max_content_primary w90" v-html="primaryTitle"></p>
    <h2 class="secondary_title max_content_primary w90" v-html="secondaryTitle"></h2>
  </div>
</template>

<script>
export default {
  name: "MainTitle",
  props: {
    primaryTitle: String,
    secondaryTitle: String,
  },
};
</script>

<style scoped lang="scss">
.title {
  width: 100%;
  padding: 1rem 0;
  p,
  h2 {
    margin: 0 auto;
  }
  p {
    color: var(--primary_color);
    margin-bottom: 0.5rem;
  }
  h2 {
    position: relative;
    color: var(--secondary_color);
    margin-bottom: 1rem;
    &:after {
      position: absolute;
      display: block;
      content: "";
      border-bottom: 2px solid var(--primary_color);
      left: 0;
      right: 0;
      bottom: -1rem;
    }
  }
}
</style>
