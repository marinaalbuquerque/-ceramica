<template>
  <div
    id="app"
    :class="{ 'has-mouse': hasMouse }"
    @touchstart="hasMouse = false"
  >
    <Flipbook
      class="flipbook"
      :pages="pages"
      :pagesHiRes="pagesHiRes"
      :startPage="pageNum"
      v-slot="flipbook"
      ref="flipbook"
      @flip-left-start="onFlipLeftStart"
      @flip-left-end="onFlipLeftEnd"
      @flip-right-start="onFlipRightStart"
      @flip-right-end="onFlipRightEnd"
      @zoom-start="onZoomStart"
      @zoom-end="onZoomEnd"
    >
      <div class="action-bar">
        <left-icon
          class="btn left"
          :class="{ disabled: !flipbook.canFlipLeft }"
          @click="flipbook.flipLeft"
        />

        <span class="page-num">
          Página {{ flipbook.page }} de {{ flipbook.numPages }}
        </span>

        <right-icon
          class="btn right"
          :class="{ disabled: !flipbook.canFlipRight }"
          @click="flipbook.flipRight"
        />
      </div>
    </Flipbook>
    <p class="credit">
      Elaborado por
      <a href="https://creactive.com.br/" target="_blank">Creactive</a>.
    </p>
  </div>
</template>

<script lang="coffee">
import 'vue-material-design-icons/styles.css'
import Ribbon from 'vue-ribbon'
import LeftIcon from 'vue-material-design-icons/ChevronLeftCircle'
import RightIcon from 'vue-material-design-icons/ChevronRightCircle'
import PlusIcon from 'vue-material-design-icons/PlusCircle'
import MinusIcon from 'vue-material-design-icons/MinusCircle'
import Flipbook from './Flipbook'

export default
  name: 'app'
  components: { Flipbook, LeftIcon, RightIcon, PlusIcon, MinusIcon, Ribbon }
  data: ->
    pages: [],
    pagesHiRes: [],
    hasMouse: true
    pageNum: null
  methods:
    onFlipLeftStart: (page) -> console.log 'flip-left-start', page
    onFlipLeftEnd: (page) ->
      console.log 'flip-left-end', page
      window.location.hash = '#' + page
    onFlipRightStart: (page) -> console.log 'flip-right-start', page
    onFlipRightEnd: (page) ->
      console.log 'flip-right-end', page
      window.location.hash = '#' + page
    onZoomStart: (zoom) -> console.log 'zoom-start', zoom
    onZoomEnd: (zoom) -> console.log 'zoom-end', zoom
    setPageFromHash: ->
      n = parseInt window.location.hash.slice(1), 10
      @pageNum = n if isFinite n
  mounted: ->
    window.addEventListener 'keydown', (ev) =>
      flipbook = @$refs.flipbook
      return unless flipbook
      flipbook.flipLeft() if ev.keyCode == 37 and flipbook.canFlipLeft
      flipbook.flipRight() if ev.keyCode == 39 and flipbook.canFlipRight

    # Simulate asynchronous pages initialization
    setTimeout (=>
      @pages = [
        null
        'images/1.png'
        'images/2.png'
        'images/3.png'
        'images/4.png'
        'images/5.png'
        'images/6.png'
        'images/7.png'
        'images/8.png'
        'images/9.png'
        'images/10.png'
        'images/11.png'
        'images/12.png'
        'images/13.png'
        'images/14.png'
        'images/15.png'
        'images/16.png'
        'images/17.png'
        'images/18.png'
        'images/19.png'
        'images/20.png'
        'images/21.png'
        'images/22.png'
        'images/23.png'
        'images/24.png'
        'images/25.png'
        'images/26.png'
        'images/27.png'
        'images/28.png'
        'images/29.png'
        'images/30.png'
        'images/31.png'
        'images/32.png'
        'images/33.png'
        'images/34.png'
        'images/35.png'
        'images/36.png'
        'images/37.png'
        'images/38.png'
        'images/39.png'
        'images/40.png'
        'images/41.png'
        'images/42.png'
        'images/43.png'
        'images/44.png'
        'images/45.png'
        'images/46.png'
        'images/47.png'
        'images/48.png'
        'images/49.png'
        'images/50.png'
        'images/51.png'
        'images/52.png'
        'images/53.png'
        'images/54.png'
        'images/55.png'
        'images/56.png'
        'images/57.png'
        'images/58.png'
        'images/59.png'
        'images/60.png'
        'images/61.png'
        'images/62.png'
        'images/63.png'
        'images/64.png'
        'images/65.png'
        'images/66.png'
      ]
      @pagesHiRes = [
        null
        'images/1.png'
        'images/2.png'
        'images/3.png'
        'images/4.png'
        'images/5.png'
        'images/6.png'
        'images/7.png'
        'images/8.png'
        'images/9.png'
        'images/10.png'
        'images/11.png'
        'images/12.png'
        'images/13.png'
        'images/14.png'
        'images/15.png'
        'images/16.png'
        'images/17.png'
        'images/18.png'
        'images/19.png'
        'images/20.png'
        'images/21.png'
        'images/22.png'
        'images/23.png'
        'images/24.png'
        'images/25.png'
        'images/26.png'
        'images/27.png'
        'images/28.png'
        'images/29.png'
        'images/30.png'
        'images/31.png'
        'images/32.png'
        'images/33.png'
        'images/34.png'
        'images/35.png'
        'images/36.png'
        'images/37.png'
        'images/38.png'
        'images/39.png'
        'images/40.png'
        'images/41.png'
        'images/42.png'
        'images/43.png'
        'images/44.png'
        'images/45.png'
        'images/46.png'
        'images/47.png'
        'images/48.png'
        'images/49.png'
        'images/50.png'
        'images/51.png'
        'images/52.png'
        'images/53.png'
        'images/54.png'
        'images/55.png'
        'images/56.png'
        'images/57.png'
        'images/58.png'
        'images/59.png'
        'images/60.png'
        'images/61.png'
        'images/62.png'
        'images/63.png'
        'images/64.png'
        'images/65.png'
        'images/66.png'
      ]
    ), 1

    window.addEventListener 'hashchange', @setPageFromHash
    @setPageFromHash()
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #f4f4f4;
  color: #333;
  overflow: hidden;
}

a {
  color: inherit;
}

.action-bar {
  width: 100%;
  height: 30px;
  padding: 10px 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.action-bar .btn {
  font-size: 30px;
  color: #666;
}

.action-bar .btn svg {
  bottom: 0;
}

.action-bar .btn:not(:first-child) {
  margin-left: 10px;
}

.has-mouse .action-bar .btn:hover {
  color: rgb(28, 28, 28);
  cursor: pointer;
}

.action-bar .btn:active {
  filter: none !important;
}

.action-bar .btn.disabled {
  color: rgb(193, 193, 193);
  pointer-events: none;
}

.action-bar .page-num {
  font-size: 12px;
  margin-left: 10px;
}

.flipbook .viewport {
  width: 90vw;
  height: calc(100vh - 50px - 40px);
}

.flipbook .bounding-box {
  box-shadow: 0 0 20px rgb(179, 179, 179);
}

.credit {
  font-size: 12px;
  line-height: 20px;
  margin: 10px;
}
</style>
