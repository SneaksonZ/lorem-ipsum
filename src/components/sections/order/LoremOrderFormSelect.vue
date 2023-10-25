<template>
    <div class="order-form-select">
        <select v-model="selectedOption" class="order-form-select__item">
            <option value="" disabled selected>Выберите тип системы</option>
            <option v-for="option in options" :value="option.value" :key="option.value">
                {{ option.text }}
            </option>
        </select>
        <span class="order-form-select-arrow"></span>
    </div>
</template>
  
<script>
export default {
    name: 'LoremOrderFormSelect',
    props: {
        options: {
            type: Array,
            required: true
        },
        value: {
            type: String || Number
        }
    },
    data() {
        return {
            isOpen: false,
            selectedOption: this.value || ''
        };
    },
    watch: {
        selectedOption(newVal) {
            this.$emit('input', newVal);
        }
    },
    methods: {
        toggleOptions() {
        this.isOpen = !this.isOpen;
        },
        selectOption(option) {
        this.selectedOption = option;
        this.isOpen = false;
        this.$emit('input', option.value);
        },
    },
}
</script>
  
<style lang="scss">
.order-form-select {
    position: relative;
    height: 100%;

    &__item {
        appearance: none;
        background-color: rgba(255, 255, 255, 0.85);
        border: 1px solid rgba(255, 255, 255, 1);
        border-radius: 3px 3px 0 0;
        width: 100%;
        font-size: 16px;
        cursor: pointer;
        height: 100%;
        max-height: 100px;
        padding: 10px;
        overflow: hidden; 
        overflow-y: auto;

        background-image: url('src/assets/icons/DropdownIcon.svg');
        background-repeat: no-repeat;
        background-position: right 10px center; /* Регулируйте позицию стрелки по вашему усмотрению */
    
    }
}



.order-form-select-arrow {
    position: absolute;
    top: 50%;
    right: 10px;
    transform: translateY(-50%);
    pointer-events: none;
    content: '\25BC'; /* Символ стрелки */
  }

  select {
    max-height: 100px; /* Максимальная высота для отображаемых строк */
    overflow-y: auto; /* Добавляем вертикальную прокрутку при необходимости */
  }
</style>
  