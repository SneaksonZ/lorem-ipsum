<script>

export default {
    name: 'LoremOrderIcon',
    components: {
    },
    props: {
        icon: {
            type: Object,
            default: null,
        }
    }
}
</script>

<template>
    <div class="order-icon">
        <component
            class="order-icon__svg"
            :is="icon"
        />
    </div>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';

.order-icon {
    position: relative;
    background-color: $order-icon-background-color;
    border: 5px solid $order-icon-border-color;
    border-radius: 50%;

    &__svg {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
}
</style>