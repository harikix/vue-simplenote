<template>
  <div class="editor">
    <Header>New Memo</Header>
    <textarea name="memo" v-model="memoBody"></textarea>
    <button @click="save">保存</button>
  </div>
</template>

<script>
import Header from "../components/Header";
export default {
  name: "new",
  components: {
    Header,
  },
  data() {
    return {
      memoBody: "",
    };
  },
  methods: {
    save() {
      this.$store.commit("save", {
        body: this.memoBody,
      });
      this.$router.push("/");
    },
  },
};
</script>

<style scoped>
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
</style>
