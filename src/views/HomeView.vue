<template>
  <div class="home">
    <div class="row">
      <div class="col-3"></div>
      <div class="col-3">
        <InstagramCard v-for="card in filteredCards" :key="card" :info="card" />
      </div>
      <div class="col-3"></div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import InstagramCard from "@/components/InstagramCard.vue";
import store from "@/store";

let cards = [
  {url:"https://picsum.photos/200/300", des:"photo", time: "sada"},
  {url: "https://picsum.photos/200", des:"photo", time: "davno"},
  {url:"https://picsum.photos/id/237/200/300", des:"dog", time: "pre sat vremena"},
  {url:"https://picsum.photos/seed/picsum/200/300", des:"photo", time: "sada"},
  {url:"https://picsum.photos/200/300?grayscale", des:"photo", time: "sada"}
];

export default {
  name: "HomeView",
  data: function () {
    return {
      cards,
      store,
    };
  },
  computed:{
    filteredCards(){
      let termin = this.store.searchTerm;
      return this.cards.filter(card => card.des.includes(termin));
    }
  },
  components: {
    InstagramCard,
  },
};
</script>
