<script>
import LoremButton from '../../.helpers/LoremButton.vue';

import LoremOrderFormInput from './LoremOrderFormInput.vue';
import LoremOrderFormSlider from './LoremOrderFormSlider.vue';
import LoremOrderFormFileInput from './LoremOrderFormFileInput.vue';

export default {
    name: 'LoremOrderForm',
    components: {
        LoremButton,
        LoremOrderFormInput,
        LoremOrderFormFileInput,
        LoremOrderFormSlider
    },
    data() {
        return {
            form: {
                action: '#',
                method: 'post',
                name: 'orderForm',
                enctype: 'multipart/form-data',
                inputs: [
                    {
                        type: 'dropdown',
                        name: 'systemType',
                        placeholder: 'Выберите тип системы',
                        value: '',
                        required: true,
                        autocomplete: true,
                    },
                    {
                        type: 'email',
                        name: 'email',
                        placeholder: 'Ваш e-mail',
                        value: '',
                        required: true,
                        autocomplete: true,
                    },
                    {
                        type: 'text',
                        name: 'name',
                        placeholder: 'Ваше имя',
                        value: '',
                        required: true,
                        autocomplete: true,
                    },
                ]
            },
            slider: {
                name: 'slider',
                value: 75, // start value
                min: 0,
                max: 100,
                step: 1
            },
            fileInput: {
                name: 'file',
                startText: 'ПРИКРЕПИТЬ ФАЙЛ'
            }
        }
    },
    methods: {
        updateSliderValue(event) {
            this.slider.value = event.target.value;
        }
    }
}
</script>

<template>
    <form 
        class="order-form"
        :action="form.action"
        :method="form.method"
        :name="form.name"
        :enctype="enctype"
        :target="target"
        :novalidate="isNovalidate"
    >
        <div class="order-form__wrapper">
            <lorem-order-form-input
                class="order-form__item"
                v-for="input in form.inputs"
                :is="input.type === 'dropdown' ? 'lorem-form-input' : 'lorem-form-input'"
                :key="input.key"
                :type="input.type"
                :name="input.name"
                :placeholder="input.placeholder"
                :value="input.value"
                :required="input.required"
                :autocomplete="input.autocomplete"
            />
            <div class="order-form-slider order-form__slider order-form__item">
                <div class="order-form-slider-header">
                    <span>Sed ut perspiciatis, unde omnis iste natus</span>
                    <span class="order-form-slider-header_percent">{{ slider.value }} %</span>
                </div>
                <lorem-order-form-slider
                    class="order-form-slider__input"
                    @input="updateSliderValue"
                    :name="slider.name"
                    :value="slider.value"
                    :min="slider.min"
                    :max="slider.max"
                    :step="slider.step"
                />
            </div>
            <lorem-order-form-file-input
                class="order-form__file"
                :fileInputText="fileInput.startText"
                :name="fileInput.name"
            />
        </div>

        <lorem-button
            class="order-form-button order-form__button"
        >
        Отправить
        </lorem-button>
    </form>
</template>

<style lang="scss"> 
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

$spaceBetweenInputs: 5;

.order-form {
    text-align: center;
    width: 100%;

    &__wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        margin: 0 em(-$spaceBetweenInputs);
    }
    
    &__item {
        min-width: em(270, $form-input-font-size);
        max-width: 100%;
        flex: 1 1 30%;
        width: 100%;
        margin: em($order-form-margin, $form-input-font-size) em($spaceBetweenInputs) 0;
    }

    &__slider {
        min-width: em(300, $form-input-font-size);
        max-width: 100%;
        flex: 1 1 50%;
        width: 100%;
        margin-top: em($order-form-margin);
    }

    &__file {
        display: flex;
        justify-content: center;
        font-size: em($form-input-file-font-size);
        font-weight: 600;
        width: em(370, $form-input-file-font-size);
        height: em(48, $form-input-file-font-size);
        margin-top: em($order-form-margin);
    }

    &__button {
        width: em(370, $button-font-size);
        margin-top: em(40, $button-font-size);
    }
}

.order-form-slider {
    &__input {
        width: 100%;
        height: em(6);
        margin-top: em(20);
    }
}

.order-form-slider-header {
    display: flex;
    justify-content: space-between;
    color: $text-color-secondary;
    font-size: em(18);

    &_percent {
        white-space: nowrap;
        padding-left: em(30, 18);
    }
}

.order-form-button {
    padding: em(17.5, $button-font-size) 0;
}



@media (max-width: px($widthSizeS)) {
    .order-form {
        &__item {
            flex: auto;
        }
        
        &__file {
            width: 100%;
        }

        &__button {
            width: 100%;
        }
    }
    .order-form__item {
        min-width: 0;
    }
}
</style>