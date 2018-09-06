<template>
  <div class="s_pageCategory">
    <h1 class="mb-3">{{category.name}}</h1>
    <CategoryListItem :category="category"/>
  </div>
</template>

<script>
import CategoryListItem from '@/components/CategoryListItem'
export default {
  props: {
    id: {
      required: true,
      type: String
    }
  },
  components: {
    CategoryListItem
  },
  computed: {
    category () {
      return this.$store.state.categories[this.id]
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
