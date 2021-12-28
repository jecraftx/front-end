<template>
<body>
  <div class="image">
    <img src="p.jpg" alt="">
    <img src="c.jpg" alt="">
    <img src="j.jpg" alt="">
  </div>
    <div class="container" v-for="(post, idx) in posts" :key="post.id">
      <b><p>{{ idx + 1 }}</p></b>
      <p id="second">{{ post.header }}</p>
      <p id="second">{{ post.content }}</p>
    </div>
</body>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      posts: [],
    };
  },
  async mounted() {
    let req = await axios.get("http://127.0.0.1:8000/api/posts");
    this.posts = req.data;
  },
};
</script>
<style scoped>
.image{
  width: 100%;
  margin-top: 5px;
  margin-bottom: 30px;
  justify-content: space-evenly;
  border: 3px yellow;
}
img{
  width: 33%;
  justify-content: space-between;
}
.container {
  display: block;
  text-align: center;
  font-size: 23px;
  justify-content: space-evenly;
  position: relative;
  font-family: Arial, Helvetica, sans-serif;
  background-color: rgb(80, 80, 114);
  border: 5px solid yellow ;
  border-radius: 30px;

}
#second{
  text-shadow: 2px 2px 5px yellow;
}
.image :nth-child(2){
  width: 29%;
}
</style>