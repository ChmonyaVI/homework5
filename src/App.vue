<template>
  <h2>Task #2</h2>
  <task-two-panel :cards-list-data="raspberryList" />
  <br />
  <h2>Task #3</h2>
  <task-three-panel :cards-list-data="notebooksList" />
  <br />
  <h2>Task #7</h2>
  <div class="wrapper">
    <searching-form @searching="onSearch" class="form" />
    <contacts-list :contacts-data="filteredContacts" />
  </div>
</template>

<script>
import taskTwoPanel from "./components/taskTwo/taskTwoPanel.vue";
import taskThreePanel from "./components/taskThree/taskThreePanel.vue";
import ContactsList from "./components/taskSeven/ContactsList.vue";
import SearchingForm from "./components/taskSeven/SearchingForm.vue";
import { raspberryList } from "./constants/2_data_raspberry.js";
import { notebooksList } from "./constants/3_data_notebooks.js";
import { contacts } from "./constants/7_data_contacts.js";

export default {
  name: "App",

  components: {
    taskTwoPanel,
    taskThreePanel,
    ContactsList,
    SearchingForm,
  },

  data() {
    return {
      raspberryList,
      notebooksList,
      contactsData: contacts,
      searchingValue: null,
    };
  },
  computed: {
    sortedContacts() {
      let sortedContacts = [...this.contactsData];
      sortedContacts.sort((a, b) => a.activity_score - b.activity_score);
      return sortedContacts;
    },
    filteredContacts() {
      let filteredContacts = this.sortedContacts;
      if (this.searchingValue) {
        filteredContacts = filteredContacts.filter((contact) => {
          if (contact.first_name || contact.last_name) {
            return (
              contact.first_name.toLowerCase().includes(this.searchingValue) ||
              contact.last_name.toLowerCase().includes(this.searchingValue)
            );
          } else return false;
        });
      }
      return filteredContacts;
    },
  },
  methods: {
    onSearch(value) {
      this.searchingValue = value;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
