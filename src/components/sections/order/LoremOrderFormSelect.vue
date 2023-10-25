<template>
  <div class="order-form-select">

    <input :value="selected" id="input-dropdown" type="text" class="order-form-select__input">
    <label
          @click="toggleOptions()"
          for="input-dropdown"
          class="order-form-select__label"
          :class="{ 'order-form-select__label_active': isOpened }">
      {{ selected }}
    </label>
    <ul v-if="isOpened" class="order-form-select__list">
      <li 
        class="order-form-select__item"
        @click="writeInput(selectedNew)"
        v-for="selectedNew in options"
      >
        {{ selectedNew }}
      </li>
    </ul>

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

  },
  data() {
    return {
      selected: 'Выберите тип системы',
      isOpened: false,

    };
  },
  methods: {
    toggleOptions() {
      this.isOpened = !this.isOpened;
    },
    writeInput: function (selectedNew) {
      this.isOpened = !this.isOpened;
      this.selected = selectedNew;
    }
  },
}
</script>

<style lang="scss">
@import 'src/assets/styles/functions.scss';

$font-size: 16;

.order-form-select {
  position: relative;
  height: 100%;

  &__item {
    appearance: none;
    display: flex;
    align-items: center;
    font-size: em($font-size);
    width: 100%;
    min-height: em(50, $font-size);
    color: rgba(255, 255, 255, 1);
    cursor: pointer;
    overflow: hidden;
    overflow-y: auto;
    padding: em(10, $font-size);
    background-color: rgba(39, 39, 51, 1);
    border: 1px solid rgba(39, 39, 51, 1);

    &:hover {
      color: rgba(66, 169, 237, 1);
    }
  }

  &__list {
    height: em(300);
    overflow: auto;
    background-color: rgba(61, 64, 80, 1);
    border: 1px solid rgba(61, 64, 80, 1);
    border-radius: 3px;

    &::-webkit-scrollbar {
      width: 7px;
    }

    &::-webkit-scrollbar-track {
      background: rgba(61, 64, 80, 1);
    }

    &::-webkit-scrollbar-thumb {
      background-color: rgba(62, 156, 220, 1);
      border-radius: 20px;
    }
  }

  &__input {
    display: none;
  }

  &__label {
    position: relative;
    display: flex;
    align-items: center;
    width: 100%;
    height: 100%;
    font-size: 1.286em;
    text-align: start;
    cursor: pointer;
    color: rgb(39, 39, 51);
    background-color: rgba(255, 255, 255, 0.85);
    border: 0.056em solid rgb(255, 255, 255);
    border-radius: 3px;
    padding: em(12) em(20) em(12) em(10);

    &_active {
      color: rgba(255, 255, 255, 1);
      background-color: rgba(61, 64, 80, 0.85);
      border: none;
    }

    &::after {
      content: '>';
      position: absolute;
      top: calc(50% - 8px);
      right: 10px;
      transform: rotate(90deg);
      transition: 0.3s linear;
      pointer-events: none;
    }


  }
}
</style>
