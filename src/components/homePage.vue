<template>
  <div class="home-main">
    <div class="header">
      <HeaderPage/>
    </div>
    <div class="content">
      <div class="leftside">
        <div
          v-for="(item,index) in menulits"
          :key="index"
          :class="item.checked"
          @click="checked(index)"
        >
          <i class="cruise" :class="item.icon"></i>
          {{item.title}}
        </div>
      </div>
      <div class="rightside">
        <div class="addSide">
          <div class="addIcon checkedStyle" @click="showDialog = true">
            <i class="cruise icon-plus"></i>Add new candidate
          </div>
          <div class="inputItem">
            <span class="checkedStyle">
              <i class="cruise icon-search"></i>
            </span>
            <input
              type="text"
              v-model="inputValue"
              v-on:keyup="search"
              placeholder="Search candidate……"
            >
          </div>
        </div>
        <div class="rightside-scroll">
          <RightSidePage ref="child"/>
        </div>
      </div>
    </div>
    <div class="cover" v-if="showDialog">
      <el-dialog title="add candidate" class="dialog" :append-to-body="true" :lock-scroll="false">
        <label>
          Candidate Name
          <input type="text" v-model="inputName">
        </label>

        <label>
          Candidate votes
          <input type="text" v-model="inputVotes">
        </label>

        <div class="dialog_foot">
          <div @click="showDialog = false" class="checkedStyle btns cancel">Cancel</div>
          <div @click="submitForm" class="checkedStyle btns">Save</div>
        </div>
      </el-dialog>
    </div>
  </div>
</template>

<script>
import HeaderPage from "./headerPage.vue";
import RightSidePage from "./rightContainPage.vue";
export default {
  name: "HomePage",
  components: {
    HeaderPage,
    RightSidePage
  },
  data() {
    return {
      inputValue: "",
      inputName: "",
      inputVotes: 0,
      showDialog: false,
      menulits: [
        { title: "DASHBOARD", icon: "icon-dashboard", checked: "checkedStyle" },
        { title: "Organizational", icon: "icon-sitemap", checked: "" },
        { title: "MY CRULISE", icon: "icon-boat", checked: "" },
        { title: "STAFF", icon: "icon-th-card", checked: "" },
        { title: "HELP", icon: "icon-life-bouy", checked: "" }
      ]
    };
  },
  methods: {
    search() {
      const val = this.inputValue;
      this.$refs.child.Search(val);
    },
    checked(index) {
      this.menulits.forEach(ele => {
        ele.checked = "";
      });
      this.menulits[index].checked = "checkedStyle";
    },
    submitForm() {
      this.showDialog = false;
      this.$refs.child.addNew(this.inputName, this.inputVotes);
    }
  }
};
</script>

<style lang="css" scoped>
@import url("../public/homePage.css");
</style>

