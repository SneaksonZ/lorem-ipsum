<script>
import LoremTextIconed from '/src/components/.helpers/LoremTextIconed.vue';

export default {
    name: 'LoremTitle',
    components: {
        LoremTextIconed
    },
    data() {
        return {
            copyright: '2018 «LoremIpsum.net» Все права защищены.',
            payments: [
                {
                    text: 'Qiwi wallet',
                    icon: 'QiwiIcon.svg'
                },
                { 
                    text: 'Yandex Money',
                    icon: 'YandexMoneyIcon.svg'
                },
                {
                    text: 'Web Money',
                    icon: 'WebMoneyIcon.svg'
                }
            ],
            contacts: [
                {
                    text: 'info@ipsum228.com',
                    href: 'https://yandex.ru/',
                    icon: 'MailIcon.svg'
                },
                {
                    text: 'Мы вконтакте',
                    href: 'https://www.google.com/',
                    icon: 'VKIcon.svg'
                }
            ]
        }
    }
}
</script>

<template>
    <footer class="footer">
        <div class="container">
            <div class="footer__wrapper">
                <div class="footer-column footer__column">
                    <div class="footer-column__copyright">
                        &copy; {{ copyright }}
                    </div>
                </div>
                <div class="footer-column footer__column">
                    <div class="footer-column-item footer-column__item"
                        v-for="payment in payments"
                    >
                        <lorem-text-iconed 
                            :iconPath="payment.icon"
                            :iconSize="payment.iconSize"
                            :iconColor="white"
                            :text="payment.text"
                            :textClassNames="'footer-column-item__payment'"
                        />
                    </div>
                </div>
                <div class="footer-column footer__column">
                    <div class="footer-column-item footer-column__item"
                        v-for="contact in contacts"
                    >
                        <lorem-text-iconed 
                            :iconPath="contact.icon"
                            :iconSize="contact.iconSize"
                            :iconColor="white"
                            :text="contact.text"
                            :textClassNames="'footer-column__link'"
                            :url="contact.href"
                        />
                    </div>
                </div>
            </div>
        </div>
    </footer>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

$font-size: 13;
$itemsMargin: 5;

.footer {
    background-color: $footer-background-color;
    color: rgba(255, 255, 255, 1);
    font-size: em(13);

    &__wrapper {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: em(25) 0;
    }

    &__column {
        margin: 0 em(-$itemsMargin);
    }
}
.footer-column {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: stretch;
    flex: 1;
    flex-wrap: wrap;
    text-align: center;
    height: 100%;
    padding: em(5);

    &__item {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        margin: em(5) em($itemsMargin);
    }

    &__link {
        color: rgba(255, 255, 255, 1);

        &:hover {
            text-decoration: underline;
        }
    }

    &:not(:last-child)::after {
        content: '';
        position: absolute;
        height: 100%;
        width: 1px;
        background-color: white;
        top: 0;
        right: 0;
    }
}

.footer-column-item {
    &__payment {
        color: rgba(195, 195, 195, 1);
    }
}

@media (max-width: px($widthSizeM)) {
    .footer {
        &__wrapper {
            flex-direction: column;
        }
    }

    .footer-column {
        &::after {
            display: none;
        }
    }
}

</style>