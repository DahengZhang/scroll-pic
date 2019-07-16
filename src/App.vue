<template>
  <div class="app">
    <goods-pic-preview :pics="pics" class="pic-preview-el"></goods-pic-preview>
  </div>
</template>

<script>
import GoodsPicPreview from './components/goods-pic-preview'

export default {
  name: 'app',
  data() {
    return {
      pics: [
        'https://pic3.zhimg.com/80/v2-cf1350583d4f89fd39a9f12390ce7dbb_hd.jpg',
        'https://pic2.zhimg.com/80/v2-ce00fd1e6e520913b52211dc21dd58d8_hd.jpg',
        'https://pic1.zhimg.com/80/v2-26f8abd7baf10854363503f495af8f24_hd.jpg',
        'https://pic1.zhimg.com/80/v2-56b6848db0d6fa5a992d68cc072dc725_hd.jpg',
        'https://pic2.zhimg.com/80/v2-b2e0594ab40bacb7a59518c3f7406d94_hd.jpg'
      ]
    }
  },
  components: {
    GoodsPicPreview
  }
}
</script>

<style lang="less">
body {
  margin: 0;
}
.app {
  .pic-preview-el {
    background-color: rgba(0, 0, 0, .2);
    width: 350px;
  }
}
</style>
