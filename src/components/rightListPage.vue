<template>
  <div>
    <div v-for="(submission,index) in submissions" :key="index" class="list-item">
      <div>
        <figure class="media-left">
          <img class="image is-64x64" :src="submission.submissionImage">
        </figure>
      </div>

      <div class="media-content">
        <div class="content">
          <p>
            <strong>
              <a :href="submission.url" class="has-text-info">{{ submission.title }}</a>
              <span class="tag is-small">#{{ submission.id }}</span>
            </strong>
            <br>
            {{ submission.description }}
            <br>
            <small class="is-size-7">
              Submitted by:
              <img class="image is-24x24" :src="submission.avatar">
            </small>
          </p>
        </div>
      </div>
      <div class="media-right">
        <span class="icon is-small" @click="clickItem('upvote',submission.id,index)">
          <i class="fa fa-chevron-up"></i>
          <strong class="has-text-info">{{ submission.votes }}</strong>
        </span>
        <span class="deleteicon" @click="clickItem('deleteItem',submission.id,index)">
          <i class="cruise icon-trash"></i>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import "../public/styles.css";
export default {
  name: "RightListPage",
  props: ["submissions"],
  data() {
    return {};
  },
  methods: {
    clickItem(type, id,index) {
      this.$emit('clickItem',type, id,index);
    }
  }
};
</script>

<style lang="css" scoped>
.list-item {
  border: 1px solid #e6e7e9;
  background-color: #f8f8f8;
  border-radius: 0.3em;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 15px;
  height: 120px;
}
.media-right {
  width: 65px;
}
.deleteicon {
  margin-left: 15px;
  cursor: pointer;
}
.deleteicon:hover {
  color: #3273dc;
}
</style>


