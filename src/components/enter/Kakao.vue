<template>
  ㅇ
</template>

<script>
import axios from 'axios';

export default {
  async created() {
    const url = process.env.VUE_APP_API_URL + 'kakao/' + this.$route.params.id;
    await axios.get(url)
    .then((result) => {
      this.$store.commit('setLoginUser', result.data)
      const loginData = JSON.stringify(result.data);
      sessionStorage.setItem("loginUser", loginData);
    })
    this.$router.push('/main');
  }
}
</script>

<style>

</style>