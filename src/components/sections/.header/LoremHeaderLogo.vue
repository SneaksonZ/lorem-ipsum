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
    color: rgba(255, 255, 255, 1);
    text-transform: uppercase;
    &_accent {
    color: rgba(66, 169, 237, 1);
    }
}

@media (max-width: px($width-size-S)) {
    .header-logo {
        font-size: 22px;
    }
}

</style>