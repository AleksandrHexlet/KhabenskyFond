<template>
  <button
    :class="[
      'popup__button',
      className,
      {
        button_disabled: disabled,
      },
    ]"
    @click="handleClick"
    :disabled="disabled"
  >
    <slot class="buttonNext__description">123456789</slot>
  </button>
</template>

<script>
export default {
  props: {
    disabled: Boolean,
    className: String,
  },
  methods: {
    handleClick(event) {
      event.preventDefault();
      if (this.disabled) {
        return;
      }
      this.$emit('custom-click');
    },
  },
};
</script>

<style scoped>
.button {
  padding: 18px 80px;
  color: #fff;
  font-size: 16px;
  background: #613a93;
  font-family: Inter;
  font-weight: 700;
  transition: opacity 0.3s;
}
.button_disabled {
  opacity: 0.3;
  cursor: not-allowed;
}

.buttonNext__description {
  display: flex;
  /* width: 16px;
  height: 10px; */
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 19px;
  text-align: center;
  color: #ffffff;
  margin: auto;
  padding: 0;
}
</style>

/* .popup__button { width: 280px; height: 52px; background: #613a93; */ } /*
.popup__button-description { */ /* width: 192px; height: 18px; font-family:
Inter; font-style: normal; font-weight: 500; font-size: 16px; line-height: 19px;
text-align: center; color: #ffffff; margin: auto; */ /* } */
