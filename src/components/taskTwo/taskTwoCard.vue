<template>
  <div>
    <div class="container">
      <a :href="cardData.link" class="card__link">
        <div class="card-img">
          <img class="img1" :src="cardData.imgSrc" />
        </div>
        <div class="card__info">
          <div class="card__info-store">
            <div class="card__logo"><img class="logo" :src="cardData.logo" /></div>
            <h4 class="card__name-store">{{ cardData.companyTitle }}</h4>
          </div>
          <div v-if="cardData.availability">
            <div class="card__availability">{{ cardData.availability }}</div>
          </div>
        </div>
        <div class="card__description-name">{{ cardData.description }}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskTwoCard",
  data() {
    return {
      available: null,
    };
  },

  props: {
    cardData: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="css" scoped>
.container {
  color: white;
  width: 300px;
  display: flex;
  flex-direction: column;
  text-align: left;
}
.card__link {
  cursor: pointer;
}
.img1 {
  width: 300px;
  height: 250px;
  border-radius: 5%;
}
.card__info {
  display: flex;
  justify-content: left;
  align-items: center;
  gap: 5px;
}
.card__info-store {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 5px;
}
.card__availability {
  color: aquamarine;
}
.card__availability::before {
  content: "•";
  color: white;
  margin-right: 3px;
}
</style>
