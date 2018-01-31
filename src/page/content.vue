<template>
  <div>
    <myHeader></myHeader>
    <h2 v-text="article.title"></h2>
    <p>作者：{{article.author.loginname}} 发表于：{{$utils.goodTime(article.create_at)}}</p>
    <hr>
    <article v-html="article.content"></article>
    <hr>
    <h3>网友回复：</h3>
    <ul>
      <li v-for="reply in article.replies" :key="reply.id">
        <p>评论者：{{reply.author.loginname}} 评论于：{{$utils.goodTime(reply.create_at)}}</p>
        <article v-html="reply.content"></article>
      </li>
    </ul>
    <myFooter></myFooter>
  </div>
</template>
<script>
import myHeader from '../components/header.vue'
import myFooter from '../components/footer.vue'
export default {
  components: {myHeader, myFooter},
  data () {
    return {
      id: this.$route.params.id,
      article: {
        author: {}
      }
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('topic/' + this.id, null, r => {
        this.article = r.data
      })
    }
  }
}
</script>
