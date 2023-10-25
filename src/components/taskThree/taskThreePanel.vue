<template>
  <div class="flex">
    <task-three-card v-for="card in cardsListData" :key="card.id" :card-data="card" />
  </div>
</template>

<script>
import taskThreeCard from "./taskThreeCard.vue";

export default {
  name: "taskThreePanel",

  components: { taskThreeCard },

  props: {
    cardsListData: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="css" scoped>
.flex {
  padding-top: 30px;
  padding-bottom: 30px;
  display: flex;
  align-items: center;
  flex-direction: column;
  text-align: left;
  gap: 15px;
  /* background-color: rgb(11, 28, 44); */
}
</style>
