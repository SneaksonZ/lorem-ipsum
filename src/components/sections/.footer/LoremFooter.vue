<script>
import QiwiIcon from '/src/assets/icons/QiwiIcon.vue';
import YandexMoneyIcon from '/src/assets/icons/YandexMoneyIcon.vue';
import WebMoneyIcon from '/src/assets/icons/WebMoneyIcon.vue';
import MessageIcon from '/src/assets/icons/MessageIcon.vue';
import VKIcon from '/src/assets/icons/VKIcon.vue';

export default {
    name: 'LoremTitle',
    data() {
        return {
            copyright: '© 2018 «LoremIpsum.net» Все права защищены.',
            payments: [
                {
                    text: 'Qiwi wallet',
                    icon: QiwiIcon,
                },
                {
                    text: 'Yandex Money',
                    icon: YandexMoneyIcon,
                },
                {
                    text: 'Web Money',
                    icon: WebMoneyIcon,
                }
            ],
            contacts: [
                {
                    text: 'info@ipsum228.com',
                    href: 'https://yandex.ru/',
                    icon: MessageIcon,
                },
                {
                    text: 'Мы вконтакте',
                    href: 'https://www.google.com/',
                    icon: VKIcon,
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
                    <p class="footer-column__copyright">
                        {{ copyright }}
                    </p>
                </div>
                <div class="footer-column footer__column">
                    <div class="footer-column-payment footer-column__payment"
                        v-for="payment in payments"

                    >
                    <component
                    class="icon"
                    :is="payment.icon"
                />
                        <span class="footer-column-payment__item"> {{ payment.text }} </span>
                    </div>
                </div>
                <div class="footer-column footer__column">
                    <div class="footer-column-payment footer-column__payment"
                        v-for="contact in contacts"
                    >
                        <component
                            class="icon"
                            :is="contact.icon"
                        />
                        <a 
                            :href="contact.href" class="footer-column__contact"> {{ contact.text }}
                        </a>
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

.footer {
    background-color: $footer-background-color;
    
    &__wrapper {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: em(30) 0;
        margin: 0 
    }
}

.footer-column {
    display: flex;
    font-size: em($font-size);
    color: rgba(255, 255, 255, 1);
    text-align: center;

    &__contact {
        color: $text-color-secondary;
    }

    &::after {
        content: '';
    }
}

.footer-column-payment {
    text-align: center;

    &__item {
        text-align: center;
    }
}

</style>