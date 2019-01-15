<template>
    <div class="recipe"></div>    
</template>
<script>
export default {
    name: "Recipe",
    props: {
        recipeId: null,
    },
    data() {
        return {
            name: "food",
            steps: null,            
        }
    }    
}
</script>

