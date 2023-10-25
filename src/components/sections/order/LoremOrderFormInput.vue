<script>
export default {
    name: 'LoremOrderFormInput',
    props: {
        type: {
            type: String,
            default: 'text'
        },
        name: {
            type: String,
            required: true
        },
        placeholder: {
            type: String,
            default: ''
        },
        value: {
            type: String,
            default: ''
        },
        required: {
            type: Boolean,
            default: false
        },
        autocomplete: {
            type: Boolean,
            default: true
        }
    }
}
</script>

<template>
    <input 
        class="order-form-input"
        :type="type"
        :name="name"
        :placeholder="placeholder"
        :value="value"
        :required="required"
        :autocomplete="autocomplete"
    />
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

.order-form-input {
    font-size: em($form-input-font-size);
    color: $form-input-color;
    background-color: $form-input-bg-color;
    border: em(1, $form-input-font-size) solid $form-input-border-color;
    border-radius: 3px;
    padding: em(12, $form-input-font-size) em(10, $form-input-font-size);

    &::placeholder {
        color: $form-input-color;
    }
}
</style>