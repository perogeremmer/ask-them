<template>
    <div
        class="page"
        :style="{
      background: bgColor
    }"
    >
        <div class="container text-center px-5 py-2">
            <div class="col-12 mb-5">
                <lottie v-if="index === 1" :options="winkLottie" :height="180" :width="180"/>
                <lottie v-else-if="index === 2" :options="monkeyLottie" :height="180" :width="180"/>
                <lottie v-else-if="index === 3" :options="cheerLottie" :height="180" :width="180"/>
                <lottie v-else-if="index === 4" :options="iceCreamLottie" :height="180" :width="180"/>

                <h3 class="mt-1">{{ message }}</h3>
                <div v-if="lastItem === index" class="btn-choice">
                    <a href="#" v-on:click="greet($event, true)" class="btn btn-md btn-success" style="background: #74b9ff !important; border-color: #74b9ff !important">Let's Go <i class="fa fa-heart"></i></a>
                    <a href="#" v-on:click="greet($event, false)" class="btn btn-md btn-danger" style="background: #c0392b !important; border-color: #c0392b !important">Meh</a>
                </div>
                <lottie v-if="isLike" :options="likeLottie" :height="165" :width="165"/>
                <lottie v-if="isUnlike" :options="unlikeLottie" :height="165" :width="165"/>
            </div>
            <div class="col-12 mt-5 mb-2">
                <div class="fixed-bottom px-5">
                    <h2 v-if="lastItem !== index"><i class="fa fa-angle-up"></i></h2>
                    <h6 v-if="lastItem === index" class="font-weight-light">Created by <a class="text-white" href="https://twitter.com/perogeremmer">Mr.Software Engineer (@perogeremmer)</a> using VueJS, Laravel, and Lottie ♥</h6>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Lottie from 'vue-lottie';
    import wink from "../../images/json/wink"
    import cheer from "../../images/json/cheer"
    import iceCream from "../../images/json/icecream"
    import monkey from "../../images/json/monkey"
    import loading from "../../images/json/loading"
    import like from "../../images/json/like"
    import unlike from "../../images/json/unlike"

    export default {
        components: {
            'lottie': Lottie
        },
        data() {
            return {
                winkLottie: {
                    animationData: wink,
                },
                iceCreamLottie: {
                    animationData: iceCream,
                },
                monkeyLottie: {
                    animationData: monkey,
                },
                cheerLottie: {
                    animationData: cheer,
                },
                loadingLottie: {
                    animationData: loading,
                },
                likeLottie: {
                    animationData: like,
                },
                unlikeLottie: {
                    animationData: unlike,
                },
                animationSpeed: 1,
                isLike: false,
                isUnlike: false
            }
        },
        props: {
            index: {
                type: Number,
                default: -1
            },
            bgColor: {
                type: String,
                default: ''
            },
            message: {
                type: String,
                default: ''
            },
            lottieImage: {
                type: String,
                default: ''
            },
            lastItem: {
                type: Number,
                default: false
            },
        },
        methods: {
            async greet(event, choice) {
                event.preventDefault();
                let _this = this;

                $(".btn-choice").remove();
                _this.getChoice(choice);
            },
            async getChoice(choice) {
                if (choice) {
                    this.isLike = true;
                } else {
                    this.isUnlike = true;
                }
            },
            async timeout(ms) {
                return new Promise(resolve => setTimeout(resolve, ms));
            }
        }
    };
</script>

<style lang="scss">
    .page {
        position: absolute;
        height: 100%;
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 100px;
        color: #fff;
    }
</style>
