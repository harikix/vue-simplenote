<template>
  <div class="home">
    <Header>My Memos</Header>
    <ul>
      <li v-for="memo in newest" :key="memo.id">
        <router-link :to="{ name: 'Edit', params: { id: memo.id } }">{{
          memo.body
        }}</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import Header from "../components/Header";
export default {
  name: "home",
  components: {
    Header,
  },
  computed: {
    newest() {
      return this.$store.state.memos.slice().reverse();
    },
  },
};
</script>

<style>
textarea {
  height: 10em;
  width: 100%;
}
button {
  border: 1px solid #333;
  background-color: #333;
  border-radius: 5px;
  color: #fff;
  padding: 10px 20px;
  margin-top: 10px;
  cursor: pointer;
}
button:hover {
  border: 1px solid #333;
  background-color: #fff;
  border-radius: 5px;
  color: #333;
}
</style>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
a {
  display: block;
  border-bottom: 1px solid #ccc;
  padding: 20px;
  color: inherit;
  text-decoration: none;
  text-align: left;
  margin-bottom: 5px;
}
</style>
