<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Animations</h1>
                <hr>
                <button class="btn btn-primary" @click="show = !show">Show Alert</button>
                <br><br>
                <!-- 一個 transition 中只能包一個 element! -->
                <!-- 幫 transition 取名 fade 後會自動依序叫用 fade-enter, fade-enter-active, fade-leave, fade-leave-active -->
                <transition name="fade">
                    <div class="alert alert-info" v-if="show">This is some info!</div>
                </transition>

                <!-- 幫 transition 取名 slide 後會自動依序叫用 slide-enter, slide-enter-active, slide-leave, slide-leave-active -->
                <transition name="slide">
                    <div class="alert alert-info" v-show="show">This is some info!</div>
                </transition>
                
                <app-mix-transition></app-mix-transition>

            </div>
        </div>
    </div>
</template>

<script>
    import MixTransition from "./MixTransition";

    export default {
        data: function() {
            return {
                show: false
            }
        },
        components: {
            appMixTransition: MixTransition
        }
    }
</script>

<!-- 每個 transition 的 css 都只會佔用 1 frame 就消失了，所以每個階段的 CSS 都要獨立宣告內容 -->
<style>
    /* 建立一個 transition 名為 fade 的classes */
    .fade-enter {
        opacity: 0;
    }
    .fade-enter-active {
        transition: opacity 1s; /* 這個css要持續1秒 */
    }
    .fade-leave {
        /** opacity: 1; */
    }
    .fade-leave-active {
        transition: opacity 1s;
        opacity: 0;
    }

    /* 建立一個 transition 名為 slide 的classes */
    .slide-enter {
        /* transform: translateY(20px); 因為與slide-in 起始位置相同，可不用寫 */
    }
    .slide-enter-active {
        animation: slide-in 1s ease-out forwards;
    }
    .slide-leave {
        
    }
    .slide-leave-active {
        animation: slide-out 1s ease-out forwards;
    }

    @keyframes slide-in {
        from {
            transform: translateY(20px);
        }
        to {
            transform: translateY(0);
        }
    }
    @keyframes slide-out {
        from {
            transform: translateY(0);
        }
        to {
            transform: translateY(20px);
        }
    }


</style>
