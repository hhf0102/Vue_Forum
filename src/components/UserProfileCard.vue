<template>
  <div class="s_userProfileCard">
    <div class="card mb-5">
      <div class="card-body">
        <div class="s_userImg">
          <img class="s_userAvatar" :src="user.avatar">
        </div>
        <div class="s_userDetail mt-3">
          <h2 class="mt-3 s_username">{{user.username}}</h2>
          <h4 class="s_name">{{user.name}}</h4>
          <span>{{user.bio ? user.bio : 'No bio specified.'}}</span>
          <br>
          <span class="text-primary fa_Globe">{{user.username}} is online</span>
        </div>
        <div class="s_postsAndThreadsCount mt-5">
          <div class="postsCount">{{userPostsCount}} {{userPostsCount === 1 ? 'post' : 'posts'}}</div>
          <div class="threadsCount">{{userThreadsCount}} {{userThreadsCount === 1 ? 'thread' : 'threads'}}</div>
        </div>
        <div class="s_userEmail mt-5">
          <i class="fas fa-globe-asia"></i> {{user.email}}
        </div>
      </div>
    </div>
    <router-link :to="{name: 'PageProfileEdit'}"><button class="btn btn-primary btn-lg btnEdit">Edit Profile</button></router-link>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      required: true,
      type: Object
    }
  },
  computed: {
    userPostsCount () {
      return this.$store.getters.postsCount(this.user['.key'])
    },
    userThreadsCount () {
      return this.$store.getters.threadsCount(this.user['.key'])
    }
  }
}
</script>

<style lang="scss" scoped>
.s_userProfileCard {
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 5px;
}
.s_userImg {
  text-align: center;
  > img {
    width: 80%;
  }
}
.s_userDetail {
  .s_username {
    font-size: 58px;
    font-weight: bold;
    text-align: center;
  }
  .s_name {
    font-size: 32px;
    font-weight: 300
  }
  .fa_Globe::before {
    content: "\f2be";
    font-family: FontAwesome;
    font-size: 14px;
    font-weight: 100;
    margin-right: 5px;
  }
}
.s_postsAndThreadsCount {
    display: flex;
    .postsCount {
      flex-basis: 50%;
      font-size: 32px;
      font-weight: 200;
      text-align: center;
    }
    .threadsCount {
      flex-basis: 50%;
      font-size: 32px;
      font-weight: 200;
      text-align: center;
    }
  }
  .s_userEmail {
    text-align: center;
  }
</style>
