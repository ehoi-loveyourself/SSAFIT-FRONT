<template>
  <div class="followBox">
    <hr />
    <div class="second">
      <div class="follow-first">
        <h3>나를 팔로잉 중인 사람</h3>
        <h3>내가 팔로우 중인 사람</h3>
      </div>
      <hr />
      <div class="follow-second">
        <div>
          <div  v-show="followerList.length === 0">팔로우 한 사람이 없습니다.</div>
          <div v-for="(follower, idx) in followerList" :key="idx">
            <div class="follow">{{ follower.nickname }}</div>
          </div>
        </div>
        <div class="border-left">
          <div style="font-size: 1.5rem;" v-show="followingList.length === 0">팔로우 한 사람이 없습니다.</div>
          <div v-for="(following, idx) in followingList" :key="idx">
            <div class="follow-third">
              <v-btn class="but" text color="error" x-large @click="unFollow(following.id)">
                unfollow
              </v-btn>
              <div class="follow">{{ following.nickname }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  computed: {
    ...mapState(["followingList", "followerList"]),
  },
  methods: {
    unFollow(followingUser) {
      this.$store.dispatch("unFollow", followingUser);
    },
  },
};
</script>

<style>
.followBox {
  width: 800px;
  margin: 0 auto;
}
.follow-first {
  display: flex;
  justify-content: space-between;
}
.follow-second {
  display: flex;
  justify-content: space-between;
}
.follow-third {
  display: flex;
  align-items: center;
}
.follow {
  height: 84px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
.but {
  margin-top: 5px;
}

</style>
