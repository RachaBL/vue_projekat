<template>
    <button @click="onClick()" :style="{ background: color }" class="btn">{{ text }}</button>
</template>

<script>
export default {
    name: 'Comp-Button',
    props: {
        text: String,
        color: String
    },
    methods: {
        onClick() {
            this.$emit('btn-click')
        }
    }
}
</script>

<style scoped>
    button {
        color: white;
        transition: .5 ease all;
    }
</style>