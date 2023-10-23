<script>
export default {
    name: 'LoremFormSlider',
    props: {
        name: {
            type: String,
            required: true,
        },
        value: {
            type: Number,
            default: 0
        },
        min: {
            type: Number,
            default: 0
        },
        max: {
            type: Number,
            default: 100
        },
        step: {
            type: Number,
            default: 1
        }
    }
}
</script>

<template>
    <input 
        class="form-slider"
        type="range"
        :name="name"
        :value="value"
        :min="min"
        :max="max"
        :step="step"
    />
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

.form-slider {
    -webkit-appearance: none;
    border: 1px solid $form-input-border-color;
    border-radius: 50px;
    background-color: $form-slider-background-color;

    &::-webkit-slider-thumb {
        -webkit-appearance: none;
        width: em(25);
        height: em(25);
        background-color: $icon-bg-color;
        border: 3px solid $icon-border-color;
        border-radius: 50%;

        &:hover {
            cursor: grab;
        }
    }
}

</style>