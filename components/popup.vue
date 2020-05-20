<template>
  <div>
    <div>
      <div :class="['modalWindow', className]">
        <div class="overlay"></div>
        <div :class="['popup', className]">
          <img
            class="icon__close"
            @click="$store.commit('popup/close')"
            src="/images/icon__close.svg"
            alt="Кнопка закрытия формы отправки сообщения"
          />
          <popupQuiz />
          <slot></slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import popupQuiz from '@/components/popupQuiz';

// import optionFirst from '@/components/ui/optionFirst';
// import optionSecond from '@/components/ui/optionSecond';
export default {
  props: ['className'],
  // components: {
  //   popupQuiz,
  // },
};
</script>

<style scoped>
.modalWindow {
  width: 100vw;
  height: 100hw;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 10;
}

.overlay {
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 12;
}
.popup {
  width: 920px;
  height: 600px;
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  top: 0px;
  left: 0px;
  width: 100vw;
  height: 100vh;
}

.popup__header {
  display: flex;
}
.popup__step {
  display: flex;
  width: 177px;
  height: 36px;
  margin: 40px 647px 40px 40px;
  font-family: Inter;
  font-style: normal;
  font-weight: 600;
  font-size: 30px;
  line-height: 36px;
  display: flex;
  align-items: flex-end;
  color: #000;
}
/* .icon__close {
  width: 20px;
  height: 20px;
  margin: 43px 42px 0px 0px;
  border: 0;
} */
.popup__question {
  display: flex;
  width: 840px;
  height: 48px;
  margin: 0px 40px 134px 40px;
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 24px;
  color: #000;
}
.popup__input {
  display: flex;
  width: 840px;
  height: 24px;
  margin: 0px 40px 10px 40px;
  font-family: Inter;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 24px;
  color: #666;
  border: 0;
}
.input__underline {
  width: 840px;
  height: 0px;
  margin: 0px 40px 200px 40px;

  border: 1px solid #e7e7e7;
  box-sizing: border-box;
}
.popup__block {
  display: flex;
  padding: 0;
}

.popupBack__button {
  display: flex;
  width: 48px;
  height: 20px;
  margin: 16px 30px 56px 40px;
  font-family: Inter;
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 19px;
  text-align: center;
  color: #c0c0c0;
  background: white;
  padding: 0;
  border: 0;
}
.popupNext__button {
  display: flex;
  width: 226px;
  height: 52px;
  margin: 0px 576px 40px 0px;
  background: #613a93;
  padding: 0;
  border: 0;
}
.popupNext__description {
  display: flex;
  width: 66px;
  height: 20px;
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 19px;
  text-align: center;
  color: #fff;
  margin: auto;
  padding: 0;
}
.icon__close {
  width: 20px;
  height: 20px;
  position: absolute;
  bottom: 739px;
  right: 299px;
  border: 0;
  cursor: pointer;
  z-index: 9999;
}

@media all and (max-width: 1279px) {
  .icon__close {
    width: 17.36px;
    top: 265px;
    left: 977px;
    position: absolute;
  }
}

@media all and (max-width: 1023px) {
  .icon__close {
    width: 17.36px;
    top: 278px;
    left: 857px;
    position: absolute;
  }
}

@media all and (max-width: 767px) {
  .icon__close {
    width: 20px;
    height: 20px;
    top: 267px;
    left: 617px;
    position: absolute;
  }
}

@media all and (max-width: 455px) {
  .icon__close {
    width: 20px;
    height: 20px;
    top: 250px;
    left: 335px;
    position: absolute;
  }
}
</style>
