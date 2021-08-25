<template>
  <!--vue에서는 이런 방식으로 prevent 사용-->
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" v-model="username" />
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password" />
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    submitForm: function () {
      // 인자로 event를 받아서 submit 시 새로고침되는 현상을 막기 위해 일반 js나 jquery에서 사용되는 방법
      // event.preventDefault();
      console.log(this.usernmae, this.password);
      var url = "https://jsonplaceholder.typicode.com/users";
      var data = {
        username: this.username,
        password: this.password,
      };
      axios
        .post(url, data) // data를 생성하거나 조작하는 http method
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>