<template>
  <div>
    <div v-for="item in popular" :key="item">
      <div class="card">
        <p>{{ item.name }}</p>
        <p>{{ item.author }}</p>
        <img :src="item.img_link" alt="" />
        <p>{{ item.price }}</p>
        <p>{{ item.description }}</p>
      </div>
    </div>
  </div>
</template>>
    
<style scoped>
img {
  width: 300px;
  height: 400px;
  object-fit: cover;
}
.card{
    margin-bottom: 50px;
}
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      popular: [],
    };
  },
  methods: {},
  mounted() {
    axios
      .get("http://localhost:3000/cathalog")
      .then((response) => (this.popular = response.data));
  },
};
</script>