<template>
  <div class="list-card">
    <a-row :gutter="16">
      <a-col :span="6" v-for="mountain in mountains" :key="mountain.id">
      <nuxtLink :to="`${mountain.continent.toLowerCase()}/${mountain.slug}`">
        <div class="card">
          <img :src="mountain.image" />
          <h3 class="card_continent">{{ mountain.continent }}</h3>
        </div>
      </nuxtLink>
      </a-col>
    </a-row>
  </div>
</template>
<script>
export default {
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start();
      setTimeout(() => this.$nuxt.$loading.finish(), 2000);
    });
  },
  async asyncData() {
    const mountains = await fetch("https://api.nuxtjs.dev/mountains").then(
      (res) => res.json()
    );
    console.log(mountains);
    return { mountains };
  },
  transition: 'slide-bottom'
};
</script>
