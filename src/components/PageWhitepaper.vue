<template>
  <toc-page :toc-visible="whitepaperTocVisible">
    <locale-menu
      slot="locale"
      path="whitepaper"
      :langs="['en-US', 'ko', 'pt', 'zh-CN']">
    </locale-menu>
    <page-nav slot="nav"></page-nav>
    <text-ko v-if="$route.params.locale === 'ko'"></text-ko>
    <text-pt v-else-if="$route.params.locale === 'pt'"></text-pt>
    <text-zh-cn v-else-if="$route.params.locale === 'zh-CN'"></text-zh-cn>
    <text-en-us v-else></text-en-us>
  </toc-page>
</template>

<script>
import { mapGetters } from 'vuex'
import ArticleBody from '@nylira/vue-article-body'
import PageNav from './PageWhitepaperNav'
import LocaleMenu from './LocaleMenu'
import TextEnUs from '../../content/en-US/WHITEPAPER.md'
import TextKo from '../../content/ko/WHITEPAPER.md'
import TextPt from '../../content/pt/WHITEPAPER.md'
import TextZhCn from '../../content/zh-CN/WHITEPAPER.md'
import TocPage from './TocPage'
export default {
  components: {
    ArticleBody,
    LocaleMenu,
    PageNav,
    TextEnUs,
    TextKo,
    TextPt,
    TextZhCn,
    TocPage
  },
  computed: {
    ...mapGetters(['whitepaperTocVisible'])
  },
  data () {
    return {
      metadata: {
        page: 'Whitepaper',
        title: `Whitepaper - ${this.$t('site.title')}`,
        desc: 'Read the whitepaper to learn everything about Cosmos: The Internet of Blockchains.'
      }
    }
  },
  head: {
    title () {
      return {
        inner: this.metadata.page,
        separator: '-',
        complement: this.$t('site.title')
      }
    },
    meta () {
      return [
        { n: 'description', c: this.metadata.desc },
        { n: 'twitter:title', c: this.metadata.title },
        { n: 'twitter:description', c: this.metadata.desc },
        { p: 'og:title', c: this.metadata.title },
        { p: 'og:description', c: this.metadata.desc }
      ]
    }
  },
  mounted () {
    if (document.documentElement.clientWidth >= 1024) {
      this.$store.commit('setWhitepaperTocVisible', true)
    }
  }
}
</script>

<style lang="stylus">
@import '../styles/variables.styl'
</style>
