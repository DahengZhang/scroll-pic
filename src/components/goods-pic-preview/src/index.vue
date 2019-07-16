<template>
    <div class="component-goods-pic-preview">
        <button @click="transformR()">前一张</button>
        <div class="pic-scroll-wrapper" :style="'transform: translate3d(' + scroll + 'px, 0, 0); width: ' + wrapperWidth + 'px'">
            <pic-frame v-for="(item, index) in pics" :key="item + index" :src="item" class="pic-item-el" :style="'width: ' + onPicWidth + 'px'" :type="'cover'" :ref="'pic'+index"></pic-frame>
        </div>
        <button @click="transformL()">后一张</button>
    </div>
</template>

<script>
import PicFrame from './pic-frame';

export default {
    name: 'GoodsPicPreview',
    props: {
        pics: {
            type: Array,
            required: true
        },
        onPicWidth: {
            type: Number,
            default: 100
        }
    },
    data() {
        return {
            index: 0,
            scroll: 0,
            wrapperWidth: 0
        };
    },
    created() {
        this.wrapperWidth = this.onPicWidth * this.pics.length;
    },
    mounted() {
        this.$elWidth = this.$el.getBoundingClientRect().width;
    },
    methods: {
        transformL() { // 向左滚动
            // 剩余可滚动部分
            const finish = this.wrapperWidth - this.$elWidth - Math.abs(this.scroll);
            if (finish <= 0) {
                return;
            }
            if (finish < this.onPicWidth) {
                // 剩余可滚动部分小于一次可滚动距离
                this.scroll -= finish;
            } else {
                this.scroll -= this.onPicWidth;
            }
        },
        transformR() { // 向右滚动
            // 
            this.scroll = this.scroll + this.onPicWidth > 0 ? 0 : this.scroll + this.onPicWidth;
        }
    },
    components: {
        PicFrame
    }
};
</script>

<style lang="less">
.component-goods-pic-preview {
    font-size: 0;
    overflow: hidden;
    .pic-scroll-wrapper {
        transition: .5s ease;
    }
}
</style>
