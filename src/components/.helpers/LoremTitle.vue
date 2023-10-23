<template>
    <h1 class="title">
        {{ text }}
        <slot></slot>
    </h1>
</template>

<script>
export default {
    name: 'LoremTitle',
    props: {
        text: {
            type: String,
            required: false,
        }
    }
}
</script>

<style lang="scss">
.title {
    text-transform: uppercase;
}
</style>