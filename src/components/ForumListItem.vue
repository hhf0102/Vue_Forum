<template>
  <div class="s_forumListItem">
    <div class="forumDetail">
      <h3 class="card-title mb-2">
        <router-link :to="{name: 'PageForum', params: {id: this.forum['.key']}}">{{forum.name}}</router-link>
      </h3>
      <p class="card-text">{{forum.description ? forum.description : 'No description.'}}</p>
    </div>
    <div class="threadsCount"><div class="countNum">{{threadsCount}}</div><span>{{threadsCount === 1 ? 'thread' : 'threads'}}</span></div>
  </div>
</template>

<script>
export default {
  props: {
    forum: {
      required: true,
      type: Object
    }
  },
  computed: {
    threadsCount () {
      if (!this.forum.threads) {
        return 0
      }
      return Object.values(this.forum.threads).length
    }
  }
}
</script>

<style lang="scss" scoped>
.s_forumListItem {
  display: flex;
  .forumDetail {
    flex-basis: 80%;
  }
  .threadsCount {
    text-align: center;
    > .countNum {
      font-size: 30px;
    }
  }
}
</style>
