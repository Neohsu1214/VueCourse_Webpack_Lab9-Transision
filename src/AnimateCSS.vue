<template>
    <div>
        <h1>Animations using Animate.CSS</h1>
        <hr>
        <button class="btn btn-primary" @click="show = !show">Hide Alert</button>
        <br><br>
        <!-- 這次不幫 transition 取名，而是直接在裡面宣告個階段 enter, enter-active, leave, leave-active 要用的CSS名稱 -->
        <!-- 要套用 AnimateCSS的語法，要記得先給定 animated 後面才接要套用的 CSS 名稱 -->
        <transition 
            appear
            enter-active-class="animated bounce"
            leave-active-class="animated shake"
        >
        
            <div class="alert alert-info" v-if="show">This is some info!</div>
        </transition>        
    </div>
</template>

<script>
export default {
    data() {
        return {
            show: false
        }
    }
}
</script>

<style scoped>

</style>