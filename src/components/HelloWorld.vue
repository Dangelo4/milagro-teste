<template>
  <div class="hello">
    <ul class="list-group list-group-flush">
      <li class="list-group-item flex-container" v-for="post in posts" :key="post.id" >
        <img :src="post.download_url" alt="thumb" class="thumbnail">
        <div>{{ post.author }}</div>
      </li>
    </ul>
  </div>
</template>

<script>

const axios = require("axios");

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      posts: [],
    };
  },
  created() {
    axios
      .get("https://picsum.photos/v2/list?page=2&limit=6")
      .then((response) => {
        console.log(response.data)
        this.posts = response.data
      })
      .catch((error) => {
        console.log(error);
      });
  },
};

</script>




<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.list-group {
  display: -ms-flexbox;
  display: flex;
  -ms-flex-direction: column;
  flex-direction: column;
  padding-left: 0;
  margin-bottom: 0;
}

.list-group-item {
  position: relative;
  display: block;
  padding: 0.75rem 1.25rem;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid rgba(0, 0, 0, 0.125);
}

.list-group-flush .list-group-item {
  border-right: 0;
  border-left: 0;
  border-radius: 0;
}

.list-group-flush:fisrt-child .list-group-item:first-child {
  border-top: 0;
}

.flex-container {
  display: flex;
  align-items: center;
}

.thumbnail {
  width: 90px ;
  height: 90px;
  border-radius: 45px;
  margin-right: 23px;
}

.list-group{
  cursor: poiter
}

.list-group-item:hover{
  background-color: #eee;
}

</style>
