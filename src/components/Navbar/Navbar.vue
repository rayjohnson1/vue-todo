<template>
    <nav class='navbar'>
        <div class='container'>
            <div class='navbar__left'>
                <h1>Todo</h1>
            </div>
            <div class='navbar__right'>

            </div>
        </div>
    </nav>
</template>




<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    
});
</script>



<style scoped lang="scss">

.navbar{
    height: 75px;
    //border: 1px solid rgb(221, 221, 221);
    box-shadow: 0 0 20px rgba(black, .1);
    width: 65%;
    margin: 0 auto;
    border-radius: 10px;

    .container{
        max-width: 1200px;
        margin: 0 auto;
        height: inherit;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    &__left {
        
        h1{
            color: black;
            margin: 0;
            padding: 0;
        }
    }
}

</style>
