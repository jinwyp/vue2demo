<template>
  <div>
    <header></header>
    <div class="article_list">
      <ul>
        <li v-for="item in list" :key="item.id">
          <time v-text="$utils.goodTime(item.create_at)"></time>
          <router-link v-bind:to="'/content/' + item.id">
            {{ item.title }}
          </router-link>
        </li>
      </ul>
    </div>
    <Footer></Footer>
  </div>
</template>
<script>
import Header from '../components/header.vue'
import Footer from '../components/footer.vue'
export default {
  components: { Header, Footer },
  data () {
    return {
      list: []
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('topics', null, r => {
        console.log(r)
        this.list = r.data
      })
    }
  }
}
</script>
<style>
  .article_list {margin: auto;}
</style>
