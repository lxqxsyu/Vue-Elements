<template>
    <div id="example">
        <div :style="{ fontSize: postFontSize + 'em' }">测试文字大小</div>
        <ButtonLarge v-on:largeFont="postFontSize++"></ButtonLarge>
    </div>
</template>
<script>

import ButtonLarge from '@/button-large'

export default {
    components: {
        ButtonLarge
    },
    name: "TestHello",
    data(){
        return {
            postFontSize: 1
        }
        
    }
}
</script>