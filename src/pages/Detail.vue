<template>
  <div class="content">

    <router-link to="/" class="back-link">
      <svg viewBox="0 0 512 512" class="back-ic"><path d="M217.9 256L345 129c9.4-9.4 9.4-24.6 0-33.9-9.4-9.4-24.6-9.3-34 0L167 239c-9.1 9.1-9.3 23.7-.7 33.1L310.9 417c4.7 4.7 10.9 7 17 7s12.3-2.3 17-7c9.4-9.4 9.4-24.6 0-33.9L217.9 256z"></path></svg>
      Back to home
    </router-link>

    <ArticleDetail
      :article="article"
      :isFullContent="true">
    </ArticleDetail>

  </div>
</template>

<script>
import {getCache} from '@/cache'
import ArticleDetail from '@/components/ArticleDetail'

const CACHE_ALL = 'articles'

export default {
  name: 'Detail',
  components: {
    ArticleDetail
  },
  data () {
    return {
    }
  },
  computed: {
    article: function () {
      return this.getDetailData(this.$route.params.slug)
    }
  },
  methods: {
    getDetailData (slug) {
      let data = getCache(CACHE_ALL)
      return data.filter(item => {
        return item.slug.indexOf(slug) >= 0
      })[0]
    }
  }
}

</script>

<style lang="scss">
@import "../assets/scss/global.scss";
figure{
  img {
    width: 100%;
    height: auto;
  }
}
figcaption{
  font-style: italic;
  text-align: center;
  color: #ccc;
}
.back-link{
  margin-left: -10px;
  text-decoration: none;
}
.back-ic{
  fill: #4DBA87;
  vertical-align: middle;
  width: 30px;
  height: 30px;
}
</style>
