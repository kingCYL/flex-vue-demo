<template>
  <div class="righContain">
    <RightListPage v-bind:submissions="showList" v-on:clickItem="itemClick"></RightListPage>
  </div>
</template>

<script >
import Data from "../assets/data.json";
import RightListPage from "./rightListPage.vue";
export default {
  name: "RightSidePage",
  components: {
    RightListPage
  },
  data() {
    return {
      dataList: [],
      showList: []
    };
  },
  mounted() {
    // 初始化
    this.dataList = Data.submissions;
    this.dataList.forEach(ele => {
      ele.submissionImage = require("../public/images/submissions/" +
        ele.submissionImage);
      ele.avatar = require("../public/images/avatars/" + ele.avatar);
    });
    this.showList = this.dataList;
    this.sortedSubmissions(this.showList);
  },

  methods: {
    // 投票  删除  搜索 重新排序
    itemClick(type, id, i) {
      if (type == "upvote") {
        this.dataList[i].votes++;
      } else {
        this.dataList.splice(i, 1);
      }

      this.sortedSubmissions(this.showList);
      this.dataList = this.showList;
    },

    Search(val) {
      this.showList = Object.assign(this.dataList);
      if (val && val.trim()) {
        console.log(val);

        this.showList = this.showList.filter(item => {
          return item["title"].toLowerCase().indexOf(val.toLowerCase()) > -1;
        });
      }
    },

    addNew(name, vote) {
      let index = Math.ceil(Math.random() * 10);
      let selected = this.showList[index];
      let item = {
        id: this.dataList.length + 1,
        title: name,
        description: selected.description,
        url: selected.url,
        votes: vote,
        avatar: selected.avatar,
        submissionImage: selected.submissionImage
      };
      this.showList.push(item);
      this.sortedSubmissions(this.showList);
      this.dataList = this.showList;
    },

    sortedSubmissions(list) {
      list.sort((a, b) => {
        return b.votes - a.votes;
      });
    }
  }
};
</script>
