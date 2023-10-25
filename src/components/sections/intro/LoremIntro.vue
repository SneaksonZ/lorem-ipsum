<script>
import LoremTitle from '../../.helpers/LoremTitle.vue';
import LoremButton from '../../.helpers/LoremButton.vue';

export default {
    name: 'LoremIntro',
    data() {
        return {
            list: {
                title: 'At vero eos et accusamus et iusto odio dignissimos ducimus!',
                items: [
                    'Totam rem aperiam eaque ipsa',
                    'Sit voluptatem accusantium doloremque laudantium',
                    'Sed ut perspiciatis, unde omnis iste natus error',
                ]
            }
        }
    },
    components: {
        LoremTitle,
        LoremButton,
    }
}
</script>

<template>
    <div class="intro">
        <img src="../../../assets/images/intro-background.jpg" alt="" class="intro__bg">
        <div class="container">
            <div class="intro__wrapper">
                <lorem-title class="intro-title intro__title">
                    <span class="intro-title_accent">Lorem ipsum</span>
                    dolor sit ametconsectetur
                    <span class="intro-title_accent">adipiscing</span>
                </lorem-title>
                <div class="intro-list-container intro__list">
                    <h3 class="intro-list__title"> {{ list.title }} </h3>
                    <ul class="intro-list" v-if="list.items.length">
                        <li
                            class="intro-list__item"
                            v-for="item in list.items"
                            :key="item.key"
                        >
                        {{ item }}
                        </li>
                    </ul>
                </div>
                <div class="intro__controls">
                    <lorem-button
                        class="intro-button intro__button"
                    >
                        <span class="intro-button__text">Заказать</span>
                    </lorem-button>

                    <lorem-button
                        class="intro-button intro__button"
                        :isPrimary="false"
                    >
                        <span class="intro-button__text">Подробнее</span>
                    </lorem-button>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

$titleContentDefault: 48;
$titleContentSizeM: 28;

$spaceBetweenButtons: 30;

$blocksTopMarginDefault: 80;
$blocksTopMarginSizeM: 40;

$fontSizeDefault: 20;
$fontSizeMobi: 16;

.intro {
    position: relative;
    overflow: hidden;

    &__wrapper {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin: em(200) 0;
    }

    &__bg {
        position: absolute;
        width: 100vw;
        max-width: calc(100%);
        height: 100%;
        object-fit: cover;
        object-position: right center;
        z-index: -1;
    }

    &__title {
        max-width: em(780, 48);
    }

    &__list {
        margin-top: em($blocksTopMarginDefault);
    }

    &__controls {
        display: flex;
        margin-top: em($blocksTopMarginDefault);
        margin: em($blocksTopMarginDefault) em(-$spaceBetweenButtons) 0;
    }

    &__button {
        width: em(183, $button-font-size);
        margin: em($spaceBetweenButtons, $button-font-size) em($spaceBetweenButtons, $button-font-size) 0
    }
}

.intro-title {
    font-size: em($titleContentDefault);
    font-weight: 700;
    line-height: em(57, $titleContentDefault);
    align-items: center;

    &_accent {
        font-family: 'Raleway', 'Lato', 'Arial', sans-serif;
        font-weight: 800;
        color: $text-color-accent;
    }
}

.intro-list {
    font-size: em($fontSizeDefault);

    &__title {
        font-size: em($fontSizeDefault);
        font-weight: 700;
        line-height: em(24, $fontSizeDefault);
        margin-bottom: em(10, $fontSizeDefault);
    }

    &__item {
        line-height: em(24, $fontSizeDefault);

        &:not(:last-child) {
            margin-bottom: em(5, $fontSizeDefault);
        }

        &:before {
            content: '-';
            padding: 0 em(10, $fontSizeDefault); 
        }
    }
}

.intro-button {
    padding: em(15, $button-font-size) 0;
}

@media (max-width: px($width-size-L)) {
    .intro {
        background-color: rgba(255, 255, 255, 0.6);
    }
}

@media (max-width: px($width-size-M)) {
    .intro {
        &__wrapper {
            margin: em(150) 0 em(50);
        }

        &__bg {
            object-position: calc(100% + 220px) center;
        }

        &__title {
            margin-top: em($blocksTopMarginSizeM);
            margin: auto;
        }

        &__list {
            margin-top: em($blocksTopMarginSizeM);
        }

        &__controls {
            justify-content: center;
            flex-wrap: wrap;
            margin: 0;
        }
    }

    .intro-list {
        font-size: em($fontSizeMobi);
    }

    .intro-title {
        font-size: em($titleContentSizeM);
        text-align: center;
    }
}
</style>