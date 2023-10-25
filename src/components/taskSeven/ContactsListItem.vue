<template>
  <article class="card">
    <div class="card__logo">{{ firstLetterLogo }}</div>
    <div class="card__body">
      <div class="card__name">{{ fullName }}</div>
      <div class="card__email">{{ contactData.emails[0] }}</div>
    </div>
  </article>
</template>

<script>
export default {
  name: "ContactsListItem",
  props: {
    contactData: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {
    fullName() {
      let fullName = "";
      this.contactData.first_name ? (fullName += `${this.contactData.first_name} `) : 0;
      this.contactData.last_name ? (fullName += `${this.contactData.last_name}`) : 0;
      !fullName ? (fullName = "Невідомий контакт") : 0;
      return fullName;
    },
    firstLetterLogo() {
      if (this.contactData.first_name !== undefined && this.contactData.last_name !== undefined) {
        return this.contactData.first_name[0] + this.contactData.last_name[0];
      } else return this.contactData.emails[0][0];
    },
  },
};
</script>

<style lang="css" scoped>
.card {
  display: flex;
  gap: 10px;
  align-content: start;
}
.card__logo {
  flex: 0 0 auto;
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  background-color: rgb(43, 226, 43);
  color: white;
}

.card__name {
  font-weight: 700;
}
</style>
