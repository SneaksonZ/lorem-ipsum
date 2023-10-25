<template>
    <button class="button"
        :class="isPrimary ? 'button_primary' : 'button_secondary'"
    >
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'LoremButton',
    props: {
        isPrimary: {
            type: Boolean,
            default: true,
        }
    }
}
</script>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

    .button {
        text-align: center;
        border-radius: 4px;
        transition: all 0.4s;
        font-size: em($button-font-size);
        line-height: em(15.6, $button-font-size);
        text-transform: uppercase;

        &_primary {
            color: rgba(255, 255, 255, 1);
            background-color: rgba(62, 156, 220, 1);
            border: 1px solid rgba(255, 255, 255, 1);
        }

        &_secondary {
            color: rgba(42, 43, 48, 1);
            background-color: rgba(255, 255, 255, 1);
            border: 1px solid rgba(111, 109, 123, 1);
        }

        &:hover:not(:disabled) {
            transform: scale(1.15) translateY(-5px);
        }

        &:disabled {
            cursor: not-allowed;
        }
    }
</style>