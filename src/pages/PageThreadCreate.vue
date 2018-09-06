<template>
  <div class="s_PageThreadCreate">
    <h1 class="mb-3">Create new thread in <span>{{forum.name}}</span></h1>
    <ThreadEditor :forumId="id"/>
  </div>
</template>

<script>
import ThreadEditor from '@/components/ThreadEditor'
export default {
  props: {
    id: {
      required: true,
      type: String
    }
  },
  components: {
    ThreadEditor
  },
  computed: {
    forum () {
      return this.$store.state.forums[this.id]
    }
  }
}
</script>

<style lang="scss" scoped>
.s_PageThreadCreate {
  h1 {
    font-size: 36px;
    font-weight: bold;
    span {
      font-style: italic;
    }
  }
}
</style>
