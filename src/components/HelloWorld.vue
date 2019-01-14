<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>Entrees</h3>
    <br>
    <v-list subheader>
        <v-list-tile
        v-for="(item, index) in entrees"
        :key="index"
        avatar
        >
            <v-list-tile-content>
                {{item.chef+ " made " + item.recipe}}}
            </v-list-tile-content>
            <br>
        </v-list-tile>
    </v-list>
  </div>
</template>

<script>
export default {
    name: "HelloWorld",
    data() {
        return {
            entrees: [
                {
                    chef: 'Pierre',
                    recipe: 'Mashed Potatoes'
                },
                {
                    chef: 'Luna',
                    recipe: 'Lasagna'
                },
                {
                    chef: 'Max',
                    recipe: 'Cheesecake'
                },
            ]
        }
    },
    props: {
        msg: String
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
