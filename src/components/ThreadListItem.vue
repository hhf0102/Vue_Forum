<template>
  <div class="card-body s_threadListItem">
    <h3 class="card-title mb-2">
      <router-link :to="{name: 'PageThread', params: {id: thread['.key']}}">{{thread.title}}</router-link>
    </h3>
    <p class="card-text">By {{user.name}}, {{thread.publishedAt | timesChange}}</p>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  props: {
    thread: {
      required: true,
      type: Object
    }
  },
  computed: {
    user () {
      return this.$store.state.users[this.thread.userId]
    }
  },
  filters: {
    timesChange (date) {
      return moment.unix(date).format('MMMM Do YYYY, h:mm:ss a')
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
