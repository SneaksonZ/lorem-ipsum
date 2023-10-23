<script>
export default {
    name: 'LoremHeaderLogo',
    
}
</script>

<template>
<a class="header-logo" href="/">
    LoremIpsum.<span class="header-logo_accent">Net</span>
</a>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

.header-logo {
    font-family: 'Raleway', 'Lato', 'Arial', sans-serif;
    font-size: em(28);
    font-weight: 800;
    line-height: em(32);
    color: $header-logo-color-primary;
    text-transform: uppercase;
    &_accent {
        color: $header-logo-color-secondary;
    }
}

@media (max-width: px($widthSizeS)) {
    .header-logo {
        font-size: 22px;
    }
}

</style>