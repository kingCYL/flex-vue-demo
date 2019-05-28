<template>
  <div class="header">
    <span>UpVote!</span>
    <div class="avatar-box">
      <div class="avatar">
        <img src="../../static/avatar.jpg" alt>
      </div>
    </div>
    <div class="avatar-icon" @click="isShowProfile = !isShowProfile">
      <i class="cruise icon-angle-down"></i>
    </div>
    <div class="profile" v-if="isShowProfile">
      <div>
        <i class="cruise icon-id-card"></i>Profile
      </div>
      <div>
        <i class="cruise icon-cog"></i>Setting
      </div>
      <div>
        <i class="cruise icon-sign-in"></i>Sign Out
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderPage",
  data() {
    return {
      isShowProfile: false
    };
  }
};
</script>

<style lang="css" scoped>
.header {
  position: relative;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 1px 2px 2px #ecf0f4;
}
.header > span {
  font-size: 27px;
  font-weight: bold;
}
.header .avatar-box {
  position: absolute;
  right: 45px;
}
.header .avatar {
  height: 40px;
  border-radius: 50%;
  overflow: hidden;
}
.avatar > img {
  width: 40px;
}
.avatar-icon {
  position: absolute;
  right: 20px;
  cursor: pointer;
}
.avatar-icon i {
  font-size: 25px;
  color: darkgray;
}
.profile {
  padding: 10px 0;
  position: absolute;
  font-size: 14px;
  right: 10px;
  top: 57px;
  width: 120px;
  border: 1px solid #f2f2f2;
  box-shadow: 0px 2px 2px #ecf0f4;
  background-color: #fff;
}
.profile > div {
  padding: 0 15px;
  height: 30px;
  line-height: 30px;
}
.profile > div i {
  margin-right: 10px;
}
.profile > div:hover {
  background-color: #ade2ca;
}
</style>
