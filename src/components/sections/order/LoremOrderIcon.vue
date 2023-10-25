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
        <SvgLoader 
            :svgFileName="iconPath"
        />
    </div>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';

.order-icon {
    position: relative;
    background-color: rgba(62, 156, 220, 1);
    border: 5px solid rgba(40, 102, 144, 1);
    border-radius: 50%;
    width: 20px;
    height: 20px;

    &__svg {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    .order-icon > svg {
        width: 20px;
    }
}
</style>