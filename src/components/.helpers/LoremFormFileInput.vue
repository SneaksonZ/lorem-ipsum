<template>
    <div>
        <label class="form-file-button form-file__button" for="fileInput"> 
            <FileIcon 
                class="form-file-button__icon"
            />
            {{ fileInputText }} 
        </label>
        <input id="fileInput" class="form-file" type="file" ref="fileInput" @change="handleFileUpload" />
    </div>
</template>
  
<script>
import FileIcon from '/src/assets/icons/FileIcon.vue';

export default {
    data() {
        return {
            fileInputText: 'ПРИКРЕПИТЬ ФАЙЛ'
        }
    },
    components: {
        FileIcon,
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
  
<style lang="scss">
@import 'src/assets/styles/variables.scss';
@import 'src/assets/styles/functions.scss';

.form-file {
    display: none;

    &__button {
        width: 100%;
        color: $text-color-primary;
        background-color: $form-input-file-bg-color;
        margin: 0 5px;
    }
}

.form-file-button {
    display: flex;
    cursor: pointer;
    text-align: center;
    align-items: center;
    justify-content: center;
    border: 2px solid $form-input-file-border-color;
    border-radius: 3px;
    padding: em(12, $form-input-file-font-size) 0;
    overflow: hidden;

    &__icon {
        margin-right: em(10, $form-input-file-font-size);
    }
}
</style>