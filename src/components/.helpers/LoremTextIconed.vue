<script>
import SvgLoader from '/src/components/.helpers/SvgLoader.vue';

export default {
    name: 'LoremTextIconed',
    components: {
        SvgLoader
    },
    props: {
        iconPath: {
            type: String,
            required: true,
        },
        iconClassNames: String,
        text: {
            type: String,
            required: true,
        },
        textClassNames: String,
        url: String,
    },
}
</script>

<template>
    <div class="text-iconed">
        <SvgLoader 
            :class="iconClassNames"
            :svgFileName="iconPath"
        />
        <span v-if="!url" class="text-iconed__span" :class="textClassNames"> {{ text }} </span>
        <a v-else :href="url" class="text-iconed__link" :class="textClassNames"> {{ text }} </a>
    </div>
</template>

<style lang="scss">
.text-iconed {
    display: flex;
    justify-content: center;
    align-items: center;

    &__span, &__link {
        margin-left: 7px;
        white-space: nowrap;
    }
}
</style>