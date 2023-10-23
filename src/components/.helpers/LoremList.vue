<template>
    <div class="list-container">
        <h3 class="list__title"> {{ title }} </h3>
        <ul class="list" v-if="items.length">
            <li
                class="list__item"
                v-for="item in items"
                :key="item.key"
            >
            {{ item }}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'LoremList',
    props: {
        title: {
            type: String,
            required: false,
        },
        items: {
            type: Object,
            required: true,
        }
    }
}
</script>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

$fontSizeDefault: 20;
$fontSizeMobi: 16;

.list {
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

@media (max-width: px($widthSizeM)) {
    .list {
        font-size: em($fontSizeMobi);
    }
}
</style>