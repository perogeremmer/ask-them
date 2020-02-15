<template>
    <swiper
        :page-transition="pageTransition"
        :loop="loop"
        :autoplay="autoplay"
        :interval="interval"
        :show-indicator="showIndicator"
        @beforeChange="beforeChange"
        @afterChange="afterChange"
    >
        <swiper-item
            v-for="(color, index) in colors"
            :key="index"
        >
            <page
                :index="index + 1"
                :bg-color="color"
            />
        </swiper-item>
    </swiper>
</template>

<script>
    import { Swiper, SwiperItem } from 'vue-h5-swiper';
    const PAGE_TRANSITIONS = [
        'glue',
        'move',
        'fade',
        'cover',
        'carousel',
        'scale',
        'cube',
        'push',
        'three'
    ];

    export default {
        components: {
            Swiper,
            SwiperItem
        },
        data() {
            return {
                colors: [
                    '#76D7C4',
                    '#F1948A',
                    '#BB8FCE',
                    '#7FB3D5'
                ],
                showIndicator: false,
                pageTransition: PAGE_TRANSITIONS[0],
                pageTransitions: PAGE_TRANSITIONS,
            };
        },
        methods: {
            beforeChange(activeIndex, oldIndex) {
                console.log(`before-change: ${activeIndex}, ${oldIndex}`);
            },
            afterChange(activeIndex, oldIndex) {
                console.log(`after-change: ${activeIndex}, ${oldIndex}`);
            }
        }
    };
</script>

<style lang="scss">
    body {
        margin: 0;
    }
    .app {
        position: relative;
        .operation {
            position: absolute;
            top: 16px;
            left: 400px;
        }
    }
</style>
