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
        <swiper-item v-for="(item, index) in data" :key="index">
            <page :index="parseInt(index) + 1"
                  :last-item="parseInt(data.length)"
                  :bg-color="item.color"
                  :message="item.message"
                  :lottie-image="item.lottie"
            />
        </swiper-item>
    </swiper>
</template>

<script>
    import {Swiper, SwiperItem} from 'vue-h5-swiper';

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
                data: [
                    {
                        "color": '#27ae60',
                        "message": "Hi, apa kabar? Nampaknya kamu sedang tidak baik-baik saja.",
                        "lottie": "",
                    },
                    {
                        "color": '#d35400',
                        "message": "Aku memang tidak bisa memberikan banyak hal untukmu, tapi aku harap ini dapat membuatmu menjadi lebih baik.",
                        "lottie": "",
                    },
                    {
                        "color": '#8e44ad',
                        "message": "Bersedih tak apa, tapi jangan berlarut-larut ya. Tenang, semua akan baik-baik saja, mari kita perbaiki ini bersama.",
                        "lottie": "",
                    },
                    {
                        "color": '#2980b9',
                        "message": "Bagaimana kalau kita makan es krim bersama sambil tertawa melupakan duka?",
                        "lottie": "",
                    },

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
