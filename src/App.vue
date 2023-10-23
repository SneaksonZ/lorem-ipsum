<script>
import LoremHeader from './components/sections/.header/LoremHeader.vue';
import LoremIntro from './components/sections/intro/LoremIntro.vue';
import LoremOrder from './components/sections/order/LoremOrder.vue';

export default {
    name: 'app',
    components: {
        LoremHeader,
        LoremIntro,
        LoremOrder,
    },
    data() {

    },
}
</script>

<template>
    <lorem-header />
    <lorem-intro />
    <lorem-order />
</template>

<style lang="scss">
@import './assets/styles/main.scss';

</style>
