<template>
  <button
    :class="['mobile-button', { 'mobile-button_type_close': isMenuOpened }]"
    @click="toggleMobile"
  ></button>
</template>

<script>
import Button from '~/components/button';
export default {
  components: { Button },
  computed: {
    isMenuOpened() {
      return this.$store.getters['mobile-menu/getMobileMenuState'];
    },
  },
  methods: {
    toggleMobile() {
      this.$store.commit('mobile-menu/toggleMobileMenu');
    },
  },
};
</script>

<style scoped>
.mobile-button {
  width: 32px;
  height: 27px;
  background-image: url('../../static/images/menu-hamburger.svg');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  background-color: transparent;
  border: none;
  cursor: pointer;
}

.mobile-button:focus {
  outline: none;
}

.mobile-button_type_close {
  background-image: url('../../static/images/menu-close.svg');
}

@media screen and (max-width: 730px) {
  .mobile-button {
    width: 26px;
    height: 22px;
  }
}
</style>
