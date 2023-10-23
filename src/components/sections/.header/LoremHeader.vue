<script>
import LoremHeaderLogo from './LoremHeaderLogo.vue';
import LoremHeaderNavItem from './LoremHeaderNavItem.vue';

export default {
    name: 'LoremHeader',
    components: {
        LoremHeaderLogo,
        LoremHeaderNavItem
    },
    data() {
        return {
            isBurgerActive: false,
            burgerActivationBreakpoint: 1250,
            links: [
                {
                    url: '#',
                    text: 'Бизнес',
                    isSelected: true,
                },
                {
                    url: '#',
                    text: 'О нас',
                    isSelected: false,
                },
                {
                    url: '#',
                    text: 'Цены',
                    isSelected: false,
                },
                {
                    url: '#',
                    text: 'Оформить заказ',
                    isSelected: false,
                },
            ],
        }
    }
}
</script>

<template>
    <header class="header">
        <div class="container">
            <div class="header__wrapper">
                <lorem-header-logo />
                <nav 
                    class="header-navigation header__navigation"
                    :class="isBurgerActive ? 'header-navigation_active' : ''"
                >
                    <lorem-header-nav-item
                        class="header-navigation__item"
                        v-for="link in links"
                        :text="link.text"
                        :url="link.url"
                    />
                </nav>
                <button class="header-navigation-burger header-navigation__burger"
                    @click="isBurgerActive = !isBurgerActive"
                    :class="isBurgerActive ? 'header-navigation-burger_active' : ''"
                >
                    <span class="header-navigation-burger__icon"></span>
                </button>
            </div>
        </div>
    </header>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

$nav-item-font-size: 13;

.header {
    position: fixed;
    width: 100%;
    height: em($header-height);
    background-color: $header-background-color;
    z-index: 10;

    &__wrapper {
        height: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        align-content: center;
    }
    

}

.header-navigation {
    display: flex;
    align-items: center;

    &__item {
        font-size: em($header-nav-item-font-size);
        color: $header-nav-item-color;
        
        &_selected {
            color: $header-nav-item-color-accent;
        }
        
        &:not(:last-child){
            margin-right: em(60 - 5, $header-nav-item-font-size); // substract padding
        }
    }

    &__burger {
        width: em(30);
        height: em(20);
        transition: 0.2s linear;

        &:before,&:after {
            content: '';
            display: block;
            width: em(30);
            height: em(20);
            transition: 0.2s linear;
        }
    }
}

.header-navigation-burger {
    position: relative;
    display: none;
    background: none;
}

@media (max-width: px($header-burger-activation-breakpoint)) {

    .header__navigation {
        margin-top: em($header-height);
    }

    .header-navigation {
        position: fixed;
        align-items: center;
        flex-direction: column;
        text-align: center;
        align-items: center;
        justify-content: center;
        top: 0;
        left: 0;
        transform: translateX(100%);
        transition: 0.3s linear;
        width: 100%;
        // height: 100%;
        background: $header-background-color;

        &__item {
            display: block;
            width: 100%;
            padding: em(30);
            border-bottom: 1px solid $header-nav-item-color;
            &:not(:last-child) {
                margin-right: 0;
            }
        }

        &_active {
            transform: translateY(0);
        }
    }
    
    
    .header-navigation-burger {
        display: block;

        &__icon {
            position: absolute;
            background-color: white;
            left: 0;
            width: 100%;
            height: em(2);
            top: em(9);
        }

        &:before,&:after {
            content:'';
            background-color: white;
            position: absolute;
            width: 100%;
            height: em(2);
            left: 0;
        }
        
        &:before {
            top: 0;
        }

        &:after {
            bottom: 0;
        }

        &_active {

            span {
                transform: scale(0);
            }

            &:before,&:after {
                background-color: $header-nav-item-color-accent;
            }

            &:before {
                transform:rotate(-45deg);
                top: em(9);
            }
            
            &:after {
                transform:rotate(45deg);
                bottom: em(9);
            }
        }
    }
}
</style>