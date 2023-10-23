<script>
import LoremHeaderLogo from './LoremHeaderLogo.vue';

export default {
    name: 'LoromHeaderNavItem',
    components: {
        LoremHeaderLogo,
    },
    props: {
        text: {
            Type: String,
            required: true,
        },
        url: {
            type: String,
            default: '#',
        },
        isSelected: {
            type: Boolean,
            default: false,
        }
    }
}
</script>

<template>
    <a 
        class="header-navigation-item"
        :href="url"
    >
        {{ text }}
    </a>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';


.header-navigation-item {
    position: relative;
    line-height: em(16);
    text-transform: uppercase;
    padding: em(5, $header-nav-item-font-size);

    &::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 0;
        height: em(2, $header-nav-item-font-size);
        background-color: $header-nav-item-color-accent;
        transition: width 0.3s;
    }

    &:hover::after {
        width: 100%;
    }
}

</style>