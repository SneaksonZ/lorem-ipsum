<script>
import LoremOrderIcon from './LoremOrderIcon.vue';

import LoremTitle from '../../.helpers/LoremTitle.vue';
import LoremButton from '../../.helpers/LoremButton.vue';
import LoremForm from '../../.helpers/LoremForm.vue';
import LoremFormInput from '../../.helpers/LoremFormInput.vue';
import LoremFormSlider from '../../.helpers/LoremFormSlider.vue';
import LoremFormFileInput from '../../.helpers/LoremFormFileInput.vue';

import SearchIcon from '/src/assets/icons/SearchIcon.vue';
import PercentIcon from '/src/assets/icons/PercentIcon.vue';
import AddFileIcon from '/src/assets/icons/AddFileIcon.vue';
import MessageIcon from '/src/assets/icons/MessageIcon.vue';
import MoneyIcon from '/src/assets/icons/MoneyIcon.vue';

export default {
    name: 'LoremOrder',
    components: {
        LoremTitle,
        LoremButton,
        LoremOrderIcon,
        LoremForm,
        LoremFormInput,
        LoremFormSlider,
        LoremFormFileInput
    },
    data() {
        return {
            steps: [
                {
                    icon: SearchIcon,
                    text: 'Lorem ipsum dolor sit amet',
                },
                {
                    icon: PercentIcon,
                    text: 'Сonsecteturadipiscing elit',
                },
                {
                    icon: AddFileIcon,
                    text: 'Sed do eiusmod tempor',
                },
                {
                    icon: MessageIcon,
                    text: 'Esse cillum dolore eu fugiat',
                },
                {
                    icon: MoneyIcon,
                    text: 'Excepteur sint occaecat cupidatat non proident',
                }
            ],
            form: {
                action: '#',
                method: 'post',
                name: 'orderForm',
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
                value: 50, // start value
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
    <header class="order">
        <img src="/src/assets/images/order-background.jpg" alt="" class="order__bg">
        <div class="container">
            <div class="order__wrapper">
                <div class="order__header">
                    <lorem-title class="order-title order__title">Оформление 
                        <span class="order-title_accent">
                            заказа
                        </span>
                    </lorem-title>
                    <h2 class="order-subtitle order__subtitle">Перед заполнением формы ознакомьтесь с нашей схемой работы!</h2>
                </div>
                <div class="order-steps order__steps">
                    <div
                        class="order-steps-item order-steps__item"
                        v-for="step in steps"
                    >
                        <lorem-order-icon
                            class="order-steps-item__icon"
                            :icon="step.icon"
                        >
                        </lorem-order-icon>
                        <span class="order-steps-item__subtitle">
                            {{ step.text }}
                        </span>
                    </div>
                </div>
                <lorem-form
                    class="order-form order__form"
                    :action="form.action"
                    :method="form.method"
                    :name="form.name"
                >
                        <component
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
                            <lorem-form-slider
                                class="order-form-slider__input"
                                @input="updateSliderValue"
                                :name="slider.name"
                                :value="slider.value"
                                :min="slider.min"
                                :max="slider.max"
                                :step="slider.step"
                            />
                        </div>
                        <lorem-form-file-input
                            class="order-form__file"
                            :fileInputText="fileInput.startText"
                            :name="fileInput.name"
                        />
                    <!-- <lorem-button
                        class="order-form-button order-form__button"
                    >
                    Отправить
                    </lorem-button> -->
                </lorem-form>
            </div>
        </div>
    </header>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

$titleContext: 36;
$subtitleContext: 18;

$spaceBetweenBlocksDefault: 80;
$spaceBetweenIcons: 20;
$spaceBetweenInputs: 5;

$inputMargin: 30;


.order {
    position: relative;

    &__bg {
        position: absolute;
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center center;
        z-index: -1;
    }

    &__wrapper {
        padding: em(120) 0;
    }

    &__header {
        text-align: center;
    }

    &__title {

    }

    &__subtitle {
        margin-top: em($subtitleContext);
    }

    &__steps {
        margin: 0 em(-$spaceBetweenIcons);
    }

    &__form {
        margin: em($spaceBetweenBlocksDefault - $inputMargin) em(-$spaceBetweenInputs) 0;
    }
}

.order-title {
    font-size: em($titleContext);
    font-weight: 800;
    color: $text-color-secondary;

    &_accent {
        color: $text-color-accent;
    }
}

.order-subtitle {
    font-size: em($subtitleContext);
    color: $order-subtitle-color;
}

.order-steps {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;

    &__item {
        min-width: em(150);
        max-width: em(190);
        width: 100%;
        margin-top: em($spaceBetweenBlocksDefault);
    }
}

.order-steps-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    color: $order-icon-color;
    padding: 0 em($spaceBetweenIcons);

    &__icon {
        width: em(100);
        height: em(100);
    }

    &__subtitle {
        margin-top: em(20);
    }
}

.order-form {
    justify-content: center;

    &__item {
        min-width: em(270, $form-input-font-size);
        max-width: 100%;
        flex: 1 1 30%;
        width: 100%;
        margin: em($inputMargin, $form-input-font-size) em($spaceBetweenInputs) 0;
    }

    &__slider {
        min-width: em(300, $form-input-font-size);
        max-width: 100%;
        flex: 1 1 50%;
        width: 100%;
        margin-top: em($inputMargin);
    }

    &__file {
        display: flex;
        justify-content: center;
        font-size: em($form-input-file-font-size);
        font-weight: 600;
        width: em(370, $form-input-file-font-size);
        height: em(48, $form-input-file-font-size);
        margin-top: em($inputMargin);
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

</style>