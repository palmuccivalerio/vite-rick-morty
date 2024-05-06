<script>
export default {
  props: {
    cardObj: Object,
  },
  computed: {
    images() {
      return this.cardObj.image;
    },
  },
};
</script>

<template>
  <div class="card">
    <img :src="images" alt="" />
    <div class="card-body">
      <h4>{{ cardObj.name }}</h4>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>