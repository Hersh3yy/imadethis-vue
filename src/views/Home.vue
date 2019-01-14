<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/chefmario.jpg" />
    <HelloWorld msg="imadethis" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  }
};
</script>
