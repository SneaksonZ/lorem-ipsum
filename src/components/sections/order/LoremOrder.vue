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
                        v-for="(step, index) in steps"
                        :key="index"
                    >
                        <lorem-order-icon
                            class="order-steps-item__icon"
                            :iconPath="step.icon"
                        />
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

$title-context: 36;
$subtitle-context: 18;

$space-between-blocks: 80;
$space-between-icons: 20;
$order-form-margin: 30;



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
        font-size: em($title-context);
        font-weight: 800;
        color: $text-color-secondary;
        
        &_accent {
            color: $text-color-accent;
        }
    }

    &__subtitle {
        margin-top: em($subtitle-context);
    }

    &__steps {
        width: 100%;
        margin: 0 em(-$space-between-icons);
    }

    &__form {
        width: 100%;
        margin-top: em($space-between-blocks - $order-form-margin);
    }
}

.order-subtitle {
    font-size: em($subtitle-context);
    color: rgba(187, 187, 187, 1);
}

.order-steps {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;

    &__item {
        flex: 1 1 20%;
        min-width: em(100);
        width: 100%;
        margin-top: em($space-between-blocks);
    }
}

.order-steps-item {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    color: rgba(255, 255, 255, 1);
    padding: 0 em($space-between-icons);

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

    &:not(:last-child)::after {
        content: '';
        position: absolute;
        width: calc(100% - 100px);
        top: 50px;
        height: 7px;
        left: calc(50% + 50px);
        transform: scale(0.8);
        z-index: -1;
        background-image: url('src/assets/images/line.png');
        background-size: cover;
    }

}

@media (max-width: px($width-size-L)) {
    .order-steps-item {
        &__icon {
            width: em(60);
            height: em(60);
        }

        &:not(:last-child)::after {
            top: 30px;
        
        }
    }
}

@media (max-width: px($width-size-M)) {
    .order-steps {
        &__item {
            flex: 1 1 50%;
            margin-top: em(calc($space-between-blocks/2));
        }
        
    }
    
    .order-steps-item {
        &::after {
            display: none;
        }
    }
}


.order {

    &__progress {
        display: flex;
        justify-content: space-evenly;
        margin-bottom: 90px;

        @media (max-width: 1330px) {
            flex-wrap: wrap;
            justify-content: space-around;
        }
    }

    &__text {
        margin-bottom: 80px;
    }

}

</style>