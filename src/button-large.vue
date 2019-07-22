<template>
    <div>
        <button v-on:click="$emit('largeFont')">Enlarge text</button>
        <button>Small Text</button>
    </div>
</template>
<script>
export default {
    name: "TestHello",
    data(){
        return {

        }
    }
}
</script>