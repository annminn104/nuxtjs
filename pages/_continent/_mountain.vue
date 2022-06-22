<template>
  <div
    class="mountain-detail"
    :style="{ 'background-image': `url(${filteredMountain.image})` }"
  >
    <a @click="goBack()">Go back</a>
    <h1>{{ filteredMountain.title }}</h1>
    <a-row type="flex">
      <a-col flex="115px">Continent:</a-col>
      <a-col flex="auto">{{ filteredMountain.continent }}</a-col>
    </a-row>
    <a-row type="flex">
      <a-col flex="115px">Country:</a-col>
      <a-col flex="auto">{{ filteredMountain.countries[0] }}</a-col>
    </a-row>
    <a-row type="flex" :style="{ 'flex-flow': 'nowrap' }">
      <a-col flex="115px">Description:</a-col>
      <a-col flex="auto">{{ filteredMountain.description }}</a-col>
    </a-row>
    <a-row type="flex">
      <a-col flex="115px">Height:</a-col>
      <a-col flex="auto">{{ filteredMountain.height }}</a-col>
    </a-row>
  </div>
</template>
<script>
export default {
  async asyncData({ params, redirect }) {
    const mountains = await fetch("https://api.nuxtjs.dev/mountains").then(
      (res) => res.json()
    );

    const filteredMountain = mountains.find(
      (el) =>
        el.continent.toLowerCase() === params.continent &&
        el.slug === params.mountain
    );
    console.log(filteredMountain);
    if (filteredMountain) {
      return {
        filteredMountain,
      };
    } else {
      redirect("/");
    }
  },
  methods: {
    goBack() {
      this.$router.go(-1);
    },
  },
};
</script>
