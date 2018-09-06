<template>
  <div class="s_userProfileCardEdit">
    <div class="card mb-3">
      <div class="card-body">
        <div class="s_userImg">
          <img class="s_userAvatar" :src="user.avatar">
        </div>
        <div class="s_userDetail mt-3">
          <input type="text" class="mb-3" v-model="editUser.username">
          <input type="text" class="mb-3" v-model="editUser.name">
          <div class="bio">
            <label for="bio">Bio:</label>
            <textarea id="bio" cols="30" rows="5" v-model="editUser.bio"></textarea>
          </div>
        </div>
        <div class="s_postsAndThreadsCount mt-5">
          <div class="s_postsCount">{{userPostsCount}} {{userPostsCount === 1 ? 'post' : 'posts'}}</div>
          <div class="s_threadsCount">{{userThreadsCount}} {{userThreadsCount === 1 ? 'thread' : 'threads'}}</div>
        </div>
        <div class="userContact mt-5">
          <div class="website mb-2">
            <label for="website">Website</label>
            <input type="text" id="website" autocomplete="off" v-model="editUser.website">
          </div>
          <div class="email mb-2">
            <label for="email">Email</label>
            <input type="text" id="email" autocomplete="off" v-model="editUser.email">
          </div>
          <div class="location mb-4">
            <label for="location">Location</label>
            <input type="text" id="location" autocomplete="off" v-model="editUser.location">
          </div>
        </div>
        <div class="btns mt-5">
          <button @click="cancel" class="btn btn-light btn-lg">Cancel</button>
          <button @click="save" class="btn btn-primary btn-lg">Save</button>
        </div>
      </div>
    </div>
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
  data () {
    return {
      editUser: {...this.user}
    }
  },
  computed: {
    userPostsCount () {
      return this.$store.getters.postsCount(this.user['.key'])
    },
    userThreadsCount () {
      return this.$store.getters.threadsCount(this.user['.key'])
    }
  },
  methods: {
    save () {
      this.$store.dispatch('updateProfile', this.editUser)
      this.$router.push({name: 'PageProfile'})
    },
    cancel () {
      this.$router.push({name: 'PageProfile'})
    }
  }
}
</script>

<style lang="scss" scoped>
.s_userProfileCardEdit {
  border-radius: 5px;
}
.s_userImg {
  text-align: center;
  > img {
    width: 80%;
  }
}
.s_userDetail {
  .bio {
    display: flex;
    flex-direction: column;
    > label {
      font-size: 25px;
    }
  }
}
.s_postsAndThreadsCount {
  display: flex;
  .s_postsCount {
    flex-basis: 50%;
    font-size: 32px;
    font-weight: 200;
    text-align: center;
  }
  .s_threadsCount {
    flex-basis: 50%;
    font-size: 32px;
    font-weight: 200;
    text-align: center;
  }
}
.btns {
  display: flex;
  justify-content: space-between;
  > button {
    width: 100px;
  }
}
</style>
