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
            color: $button-text-color-primary;
            background-color: $button-bg-color-primary;
            border: 1px solid $button-border-color-primary;
        }

        &_secondary {
            color: $button-text-color-secondary;
            background-color: $button-bg-color-secondary;
            border: 1px solid $button-border-color-secondary;
        }

        &:hover:not(:disabled) {
            transform: scale(1.15) translateY(-5px);
        }

        &:disabled {
            cursor: not-allowed;
        }
    }
</style>