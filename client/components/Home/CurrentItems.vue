<!--
Homepage widgets for items you're currently borrowing and lending
-->
<template>
  <section id="current_items">
    <!--Currently borrowing (only appears if you're currently borrowing something)-->
    <section>
      <h2>currently borrowing ({{ $store.state.activeBorrows.filter(handoff => handoff.borrower === $store.state.username).length }})</h2>
      <p>post an update about the item(s) you're borrowing!</p>
      <GalleryComponent num-columns="4">
        <HandoffComponent
          v-for="handoff in $store.state.activeBorrows.filter(handoff => handoff.borrower === $store.state.username)"
          :key="handoff._id"
        />
      </GalleryComponent>
    </section>

    <!--Currently lending (only appears if you're currently lending something)-->
    <section>
      <h2>currently lending ({{ $store.state.activeBorrows.filter(handoff => handoff.owner === $store.state.username).length }})</h2>
      <GalleryComponent num-columns="4">
        <HandoffComponent
          v-for="handoff in $store.state.activeBorrows.filter(handoff => handoff.borrower === $store.state.username)"
          :key="handoff._id"
        />
      </GalleryComponent>
    </section>
  </section>
</template>

<script>
import GalleryComponent from "@/components/util/GalleryComponent.vue";
import HandoffComponent from "@/components/Handoff/HandoffComponent.vue";

export default {
  name: "CurrentItems",
  components: {
    GalleryComponent,
    HandoffComponent
  },
}
</script>

<style scoped>
#current_items {
  display: flex;
  margin-bottom: 3rem;
}
</style>