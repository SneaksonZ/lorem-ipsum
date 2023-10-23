<script>
export default {
    name: 'LoremForm',
    props: {
        action: {
            type: String,
            default: '#'
        },
        method: {
            type: String,
            default: 'post'
        },
        name: {
            type: String,
        },
        enctype: {
            type: String,
            default: 'multipart/form-data'
        },
        target: {
            type: String,
        },
        isNovalidate: {
            type: Boolean,
            default: false,
        }
    }
}
</script>

<template>
    <form 
        class="form"
        :action="action"
        :method="method"
        :name="name"
        :enctype="enctype"
        :target="target"
        :novalidate="isNovalidate"
    >
        <div class="form__wrapper">
            <slot></slot>            
        </div>
    </form>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

.form {
    display: flex;
    flex-direction: column;
    
    &__wrapper {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }
}

@media (max-width: px($widthSizeL)) {
    .form {
        &__wrapper {
            justify-content: center;
            align-items: center;
        }
    }
}

</style>