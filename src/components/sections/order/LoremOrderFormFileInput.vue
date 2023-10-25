<script>
import LoremTextIconed from '../../.helpers/LoremTextIconed.vue';

export default {
    data() {
        return {
            fileInputText: 'ПРИКРЕПИТЬ ФАЙЛ',
            icon: 'FileIcon.svg'
        }
    },
    components: {
        LoremTextIconed,
    },
    methods: {
        handleFileUpload() {
            const file = this.$refs.fileInput.files[0];
            const fileName = file.name;
            this.fileInputText = fileName;
        }
    }
}
</script>
  
<template>
    <div>
        <label class="order-form-file-button order-form-file__button" for="fileInput"> 
            <lorem-text-iconed 
                :iconPath="icon"
                :text="fileInputText"
            />
        </label>
        <input id="fileInput" class="order-form-file" type="file" ref="fileInput" @change="handleFileUpload" />
    </div>
</template>

<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

.order-form-file {
    display: none;

    &__button {
        width: 100%;
        color: $text-color-primary;
        background-color: rgba(255, 255, 255, 1);
        margin: 0 5px;
    }
}

.order-form-file-button {
    display: flex;
    cursor: pointer;
    text-align: center;
    align-items: center;
    justify-content: center;
    border: 2px solid rgba(62, 156, 220, 1);
    border-radius: 3px;
    padding: em(12, $form-input-file-font-size) 0;
    overflow: hidden;


}
</style>