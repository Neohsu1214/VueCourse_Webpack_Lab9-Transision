<template>
    <div>
        <h1>Mix Animations</h1>
        <hr>
        <button class="btn btn-primary" @click="show">Hide Alert</button>
        <br><br>
        <!-- 幫 transition 取名 mix 後會自動依序叫用 mix-enter, mix-enter-active, mix-leave, mix-leave-active -->
        <transition name="mix" appear>
            <div class="alert alert-info" v-if="!show">This is some info!</div>
        </transition>
        <!-- transition 加上 appear 可於網頁一開始就執行一次 -->
    </div>
</template>

<script>
export default {
    data() {
        return {
            show: true
        }
    }
}
</script>

<style scoped>
    /* 建立一個 transition 名為 mix 的classes */
    .mix-enter {
        /* transform: translateY(20px); 因為與slide-in 起始位置相同，可不用寫 */
        opacity: 0;
    }
    .mix-enter-active {
        animation: slide-in 1s ease-out forwards;
        /* 以下也可以定義到 slide-in 去 */
        transition: opacity .5s; 
    }
    .mix-leave {
        
    }
    .mix-leave-active {
        animation: slide-out 1s ease-out forwards;
        /* 以下也可以定義到 slide-in 去 */
        transition: opacity 3s;
        opacity: 0;
        /* 設定在同一個css中的動作長度可以多嘗試多拿捏 */
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