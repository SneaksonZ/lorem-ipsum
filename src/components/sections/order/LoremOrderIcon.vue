<script>
import SvgLoader from '../../.helpers/SvgLoader.vue';

export default {
    name: 'LoremOrderIcon',
    components: {
        SvgLoader
    },
    props: {
        iconPath: {
            type: String,
            required: true,
        },
    },

}
</script>

<template>
    <div class="order-icon">
        <component
            class="order-icon__svg"
            :is="icon"
        />
        <SvgLoader 
            :svgFileName="iconPath"
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
    width: 20px;
    height: 20px;

    &__svg {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
}
</style>