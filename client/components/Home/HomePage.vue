<template>
  <main style="display:flex-col">
    <FeedPage v-if="$store.state.username" style=""/>
    <NonAuthedHomePage v-else />
  </main>
</template>

<script>
import NonAuthedHomePage from '@/components/Home/NonAuthedHomePage.vue';
import AuthedHomePage from '@/components/Home/AuthedHomePage.vue';
import FeedPage from '@/components/Home/FeedPage.vue';

export default {
  name: 'HomePage',
  components: {
    NonAuthedHomePage,
    AuthedHomePage, 
    FeedPage
  }
};
</script>