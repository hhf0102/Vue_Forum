<template>
  <div class="card-body">
    <ForumListItem
    v-for="forum in forums"
    :forum="forum"
    :key="forum['.key']"
    />
  </div>
</template>

<script>
import ForumListItem from '@/components/ForumListItem'
export default {
  props: {
    forums: {
      required: true,
      type: Array
    }
  },
  components: {
    ForumListItem
  }
}
</script>

<style lang="scss" scoped>

</style>
