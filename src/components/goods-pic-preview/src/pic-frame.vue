<template>
    <div class="component-pic-frame">
        <div class="frame-container">
            <div class="pic-container">
                <img :src="src" class="pic-el" :class="type">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PicFrame',
    props: {
        src: {
            type: String,
            required: true
        },
        type: { // contain cover
            type: String,
            default: 'contain'
        }
    }
}
</script>

<style lang="less">
.component-pic-frame {
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    .frame-container {
        padding-top: 100%;
        position: relative;
        .pic-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, .5);
            .pic-el {
                width: 100%;
                height: 100%;
                &.cover {
                    object-fit: cover;
                }
                &.contain {
                    object-fit: contain;
                }
            }
        }
    }
}
</style>
