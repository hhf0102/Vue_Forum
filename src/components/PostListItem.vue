<template>
  <div class="card mb-3 s_postListItem">
    <div class="card-body">
      <div class="s_userDetail">
        <div class="s_userName text-center mb-2">{{user.username}}</div>
        <div class="text-center">
          <img class="s_userAvatar" :src="user.avatar" alt="" width="130" height="130">
        </div>
        <div class="s_threadsCount mt-3">{{userThreadsCount}} {{userThreadsCount === 1 ? 'thread' : 'threads'}}</div>
        <div class="s_postsCount mt-2">{{userPostsCount}} {{userPostsCount === 1 ? 'post' : 'posts'}}</div>
      </div>
      <div class="s_postContent">
        <p class="s_text">{{post.text}}</p>
        <div class="s_datePostListItem">{{post.publishedAt | timesChange}}</div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  props: {
    post: {
      required: true,
      type: Object
    }
  },
  computed: {
    user () {
      return this.$store.state.users[this.post.userId]
    },
    userThreadsCount () {
      return this.$store.getters.threadsCount(this.user['.key'])
    },
    userPostsCount () {
      return this.$store.getters.postsCount(this.user['.key'])
    }
  },
  filters: {
    timesChange (date) {
      return moment.unix(date).fromNow()
    }
  }
}
</script>

<style lang="scss" scoped>
.card-body {
  min-height: 300px;
  display: flex;
}
.s_userDetail {
  text-align: center;
  flex-basis: 20%;
  .s_userName {
    font-size: 25px;
    color: $primary-color;
  }
  .s_threadsCount {
    font-size: 20px;
  }
  .s_postsCount {
    font-size: 20px;
  }
}
.s_postContent {
  flex-basis: 80%;
  display: flex;
  flex-direction: column;
  .s_text {
    font-size: 20px;
  }
  .s_datePostListItem {
    flex: 1;
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
  }
}
</style>
