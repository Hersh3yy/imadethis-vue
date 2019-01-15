<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/chefmario.jpg" />
    <Entrees msg="imadethis" />
  </div>
</template>

<script>
// @ is an alias to /src
import Entrees from "@/components/Entrees.vue";

export default {
    name: "home",
    components: {
        Entrees
    }
};
</script>
