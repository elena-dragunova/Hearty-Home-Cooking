<template>
  <div>
    <app-category
      v-for="category in categories"
      :key="category.id"
      :category="category" />
  </div>
</template>

<script>
import axios from 'axios'
import Category from '../components/Category'

export default {
  components: {
    'app-category': Category
  },
  asyncData({ req, params }) {
    return axios.get('http://localhost:3001/categories').then(res => {
      return {
        categories: res.data
      }
    })
  }
}
</script>

<style>
</style>
