
<template>

  <div>
<!--    <hero />-->
<!--    <hr />-->
    <home-content />
  </div>
</template>

<script>
import Hero from "../components/Hero";
import HomeContent from "../components/HomeContent";

export default {
  name: "home",
  data(){
    return {
      token: undefined
    }

  },methods: {
    isAuthenticated() {
      return !!this.token;
    }
  },
  async mounted() {
    const token = await this.$auth.getIdTokenClaims();
    // eslint-disable-next-line no-console
    console.log('token', token.__raw);

    this.token= token.__raw || 'no token';


  },
  components: {
    Hero,
    HomeContent
  }
};
</script>

<style lang="scss" scoped>
.next-steps {
  .fa-link {
    margin-right: 5px;
  }
}
</style>
