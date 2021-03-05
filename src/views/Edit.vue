<template>
  <div class="editor">
    <Header>Edit Memo</Header>
    <textarea name="memo" v-model="memoBody"></textarea>
    <button @click="save">保存</button>
    <button class="remove" @click="remove">削除</button>
  </div>
</template>

<script>
import Header from "../components/Header.vue";
export default {
  name: "edit",
  components: {
    Header,
  },
  data() {
    return {
      memoBody: "",
    };
  },
  mounted() {
    let id = this.$route.params["id"];
    let memo = this.$store.state.memos.slice().find((memo) => memo.id == id);
    this.memoBody = memo.body;
  },
  computed: {
    memo() {
      let id = this.$route.params["id"];
      return this.$store.state.memos.find((memo) => memo.id == id);
    },
  },
  methods: {
    save() {
      this.$store.commit("update", {
        id: this.$route.params["id"],
        body: this.memoBody,
      });
      this.$router.push("/");
    },
    remove() {
      this.$store.commit("remove", this.$route.params["id"]);
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
.remove {
  background-color: transparent;
  color: #f33;
  border: none;
}
</style>
