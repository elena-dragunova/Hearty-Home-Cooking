<template>
  <div>
    <app-recipe
      v-for="recipe in recipes"
      :key="recipe.id"
      :recipe="recipe"/>
  </div>
</template>
<script>
import axios from 'axios'
import Recipe from '../../components/Recipe'

export default {
  validate({ params }) {
    return !isNaN(+params.id)
  },
  asyncData({ req, params }) {
    return axios
      .get(`http://localhost:3001/recipes?categoryId=${params.id}`)
      .then(res => {
        return {
          recipes: res.data
        }
      })
  },
  components: {
    'app-recipe': Recipe
  }
}
</script>

<style scoped>
</style>
