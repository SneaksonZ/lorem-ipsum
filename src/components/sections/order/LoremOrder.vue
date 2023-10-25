<script>
import LoremOrderIcon from './LoremOrderIcon.vue';
import LoremOrderForm from './LoremOrderForm.vue';

import LoremTitle from '../../.helpers/LoremTitle.vue';
import LoremButton from '../../.helpers/LoremButton.vue';

export default {
    name: 'LoremOrder',
    components: {
        LoremTitle,
        LoremButton,
        LoremOrderIcon,
        LoremOrderForm,
    },
    data() {
        return {
            steps: [
                {
                    icon: 'SearchIcon.svg',
                    text: 'Lorem ipsum dolor sit amet',
                },
                {
                    icon: 'PercentIcon.svg',
                    text: 'Consecteturadipiscing elit',
                },
                {
                    icon: 'AddFileIcon.svg',
                    text: 'Sed do eiusmod tempor',
                },
                {
                    icon: 'MessageIcon.svg',
                    text: 'Esse cillum dolore eu fugiat',
                },
                {
                    icon: 'MoneyIcon.svg',
                    text: 'Excepteur sint occaecat cupidatat non proident',
                }
            ],
        }
    },

}
</script>

<template>
    <header class="order">
        <img src="/src/assets/images/order-background.jpg" alt="" class="order__bg">
        <div class="container">
            <div class="order__wrapper">
                <div class="order__header">
                    <lorem-title class="order-title order__title">Оформление 
                        <span class="order__title_accent">
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
                            :iconPath="step.icon"
                        >
                        </lorem-order-icon>
                        <span class="order-steps-item__subtitle">
                            {{ step.text }}
                        </span>
                    </div>
                </div>
                <lorem-order-form />
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
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: em(120) 0 em(150);
    }

    &__header {
        text-align: center;
    }

    &__title {
        font-size: em($titleContext);
        font-weight: 800;
        color: $text-color-secondary;
        
        &_accent {
            color: $text-color-accent;
        }
    }

    &__subtitle {
        margin-top: em($subtitleContext);
    }

    &__steps {
        width: 100%;
        margin: 0 em(-$spaceBetweenIcons);
    }

    &__form {
        width: 100%;
        margin-top: em($spaceBetweenBlocksDefault - $order-form-margin);
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
        display: flex;
        justify-content: center;
        align-items: center;
        width: em(100);
        height: em(100);
    }

    &__subtitle {
        margin-top: em(20);
    }
}

</style>