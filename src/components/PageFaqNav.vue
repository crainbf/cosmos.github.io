<template>
  <div class="page-faq-nav mobile-only">
    <toc-hidden-bar
      v-show="!faqTocVisible"
      @click.native="tocVisible(true)"
      icon="list-ol">
    </toc-hidden-bar>
    <toc-hidden-bar
      v-show="faqTocVisible"
      @click.native="tocVisible(false)"
      icon="times">
    </toc-hidden-bar>
  </div>
</template>

<script>
import Ps from 'perfect-scrollbar'
import watchTocClicks from '../scripts/watchTocClicks.js'
import inViewport from '../scripts/inViewport.js'
import visibleTocActivate from '../scripts/visibleTocActivate.js'
import percentageScrolling from '../scripts/percentageScrolling.js'
import TocHiddenBar from './TocHiddenBar'
import { mapGetters } from 'vuex'
export default {
  name: 'page-faq-nav',
  components: {
    TocHiddenBar
  },
  computed: {
    ...mapGetters(['faqTocVisible', 'faqElementsVisible'])
  },
  methods: {
    setTocVisOnWidth () {
      let width = document.documentElement.clientWidth
      if (width >= 1024) {
        this.tocVisible(true)
      } else {
        this.tocVisible(false)
      }
    },
    tocVisible (value) {
      if (value) {
        document.querySelector('.minimal-toc').style.display = 'block'
        this.initToc()
      } else {
        document.querySelector('.minimal-toc').style.display = 'none'
        this.destroyToc()
      }
    },
    initToc () {
      Ps.initialize(document.querySelector('.minimal-toc'))
      this.$store.commit('setFaqTocVisible', true)

      watchTocClicks(this.tocVisible)
      this.$store.commit('setFaqElementsVisible',
        inViewport(document.querySelectorAll('h2, h3, h4, h5')))
      percentageScrolling()
    },
    destroyToc () {
      Ps.destroy(document.querySelector('.minimal-toc'))
      this.$store.commit('setFaqTocVisible', false)
    }
  },
  mounted () {
    this.setTocVisOnWidth()
  },
  watch: {
    faqElementsVisible () {
      visibleTocActivate(this.faqElementsVisible)
    },
    '$route.params.locale' () {
      setTimeout(() => this.setTocVisOnWidth(), 100)
    }
  }
}
</script>
