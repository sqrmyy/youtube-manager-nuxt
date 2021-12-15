<template>
  <section class="section">
    <div class="container">
      <div class="block">
        <div v-for="(item, key) in items" :key="key" class="block">
          <AppVideo :item="item" :video-id="item.id" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ROUTES from '~/routes/api'
import AppVideo from '~/components/AppVideo'
export default {
  components: {
    AppVideo,
  },
  async fetch({ store }) {
    const payload = {
      uri: ROUTES.GET.FAVORITE,
    }
    await store.dispatch('fetchFavoriteVideos', payload)
  },
  computed: {
    items() {
      return this.$store.getters.getFavoriteVideos
    },
  },
}
</script>
