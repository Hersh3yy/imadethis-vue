<template>
    <div class="entree">
        <h1>{{chef ? chef : "i"}} made {{recipe.name ? recipe.name : "something yummy"}}</h1>
        <v-container>
            <v-layout row wrap>
                Recipe: {{recipeId}}
                <v-btn @click="loadRecipe">Load recipe</v-btn>
                <v-btn @click="recipeId = 0">Clear recipe</v-btn>
                <v-flex xs12 md6>
                    <v-text-field placeholder="Chef name" v-model="chef"/>
                    <v-text-field placeholder="Entree name" v-model="entreeName"/>
                    <div class="file-upload-form">
                        Upload an image file:
                        <input type="file" @change="previewImage" accept="image/*">
                    </div>
                    <div class="image-preview" v-if="entreeImage.length > 0">
                        <img class="preview" :src="entreeImage">
                    </div>
                    <v-textarea
                        outline
                        name="input-7-4"
                        placeholder="Chef notes"
                        v-model="chefNotes"
                    ></v-textarea>
                    <v-btn @click="postEntree">Post entree</v-btn>
                </v-flex>
            </v-layout>
        </v-container>        
    </div>
</template>
<script>
import axios from "axios";
export default {
    name: "Entree",
    props: {
        entreeId: Number,
        initialRecipeId: Number,
    },
    data() {
        return {
            chef: null,
            entreeName: null,
            entreeImage: "",
            chefNotes: null,
            recipeId: this.initialRecipeId,
            recipe: {
                name: null,
            }
        }
    },
    methods: {
        loadRecipe() {
            this.recipeId++;
        },
        previewImage(event) {
            var input = event.target;
            if (input.files && input.files[0]) {
                var reader = new FileReader();
                // Define a callback function to run, when FileReader finishes its job
                reader.onload = (e) => {
                    this.entreeImage = e.target.result;
                }
                reader.readAsDataURL(input.files[0]);
            }
        },
        postEntree () {
            let data = {
                recipe_id: this.recipeId,
                entree_name: this.entreeName,
                chef: this.chef,
                image: this.entreeImage,
                notes: this.notes,
            };
            axios.post('http://localhost:8000/entrees', data)
            .then(response => {
                console.log(response)
            }).catch(e => {
                console.error(e);
            });
        }
    },
    watch: {
        recipeId: {
            immediate: true,
            handler(value) {
                console.log('coming soon: GET recipe/' + value);
            },
        },
    }
}
</script>
<style lang="scss">
.file-upload-form, .image-preview {
    font-family: "Helvetica Neue",Helvetica,Arial,sans-serif;
    padding: 20px;
}
img.preview {
    width: 200px;
    background-color: white;
    border: 1px solid #DDD;
    padding: 5px;
}
</style>


