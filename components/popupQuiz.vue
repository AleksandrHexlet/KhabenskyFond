<template>
  <div class="popupQuiz">
    <h3 class="popup__step">
      {{ currentQuestion.step }}
    </h3>
    <!-- <img
      class="icon__close"
      @click="$store.commit('popup/close')"
      src="/images/icon__close.svg"
      alt="Кнопка закрытия формы отправки сообщения"
    /> -->

    <p class="popup__questions_block">
      <span class="popup__question">{{ currentQuestion.question }}</span>
      <span
        v-if="currentQuestion.questionAdditional"
        class="popup__questionAdditional"
      >
        {{ currentQuestion.questionAdditional }}</span
      >
    </p>

    <Input placeholder="Напишите тут" :bottomBorder="true" v-model="answer" />
    <div class="button__block">
      <Button @custom-click="prevQuestion" class="buttonBack" type="button"
        >Назад</Button
      >

      <Button @custom-click="nextQuestion" class="buttonNext" type="button">
        <!-- <p class="buttonNext__description"></p> -->
      </Button>
    </div>
  </div>
</template>

<script>
import Input from '~/components/ui/Input';
import button from '~/components/button';

export default {
  props: {
    step: {
      required: true,
      default: 'Что-то пошло не так !',
      type: String,
    },
    question: {
      required: true,
      type: String,
    },
  },
  components: {
    Input,
    Button: button,
  },
  data() {
    return {
      answer: '',
    };
  },
  computed: {
    currentQuestion() {
      const { popupQuiz } = this.$store.state;
      const { currentQuestion, questions } = popupQuiz;
      return questions[currentQuestion] || '';
    },
    initialAnswer() {
      const { popupQuiz } = this.$store.state;
      const { currentQuestion, answers } = popupQuiz;
      return answers[currentQuestion] || '';
    },
  },
  methods: {
    async nextQuestion() {
      await this.$store.dispatch('popupQuiz/NEXT_QUESTION', {
        answer: this.answer,
      });
      this.answer = this.initialAnswer;
    },
    async prevQuestion() {
      await this.$store.dispatch('popupQuiz/PREV_QUESTION');
      this.answer = this.initialAnswer;
    },
  },
};
</script>

<style scoped>
.popupQuiz {
  width: 920px;
  height: 600px;
  background: #ffffff;
  justify-content: center;
  align-items: center;
  margin: auto;
  z-index: 123;
  position: fixed;
}

.popup__step {
  display: flex;
  width: 177px;
  height: 36px;
  margin: 40px 647px 40px 40px;
  font-family: Inter;
  font-style: normal;
  font-weight: 600;
  font-size: 27px;
  line-height: 36px;
  display: flex;
  align-items: flex-end;
  color: #000000;
}
.popup__questions_block {
  display: inline-block;
  width: 840px;
  height: 24px;
  margin: 0px 40px 134px 40px;
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 24px;
  color: #000000;
  text-align: left;
}
.popup__question {
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 24px;
  color: #000000;
  text-align: left;
}
.popup__questionAdditional {
  font-family: Inter;
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 24px;
  color: #000000;
  text-align: left;
  opacity: 0.5;
}
.button__block {
  display: flex;
  padding: 0;
}

.buttonBack {
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
  cursor: pointer;
}
.buttonNext {
  display: flex;
  width: 226px;
  height: 52px;
  margin: 0px 576px 40px 0px;
  background: #613a93;
  padding: 0;
  border: 0;
  cursor: pointer;
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

.icon__close {
  width: 20px;
  height: 20px;
  position: relative;
  bottom: 79px;
  left: 870px;
  border: 0;
  cursor: pointer;
}

@media all and (max-width: 1279px) {
  .popupQuiz {
    max-width: 800px;
    height: 520px;
    display: flex;
    flex-direction: column;
  }

  .popup__step {
    height: 32px;
    max-width: 155px;
    height: 36px;
    margin: 40px 605px 40px 40px;
    font-weight: 600;
    font-size: 24px;
    line-height: 32px;
  }

  .popup__questions_block {
    max-width: 720px;
    height: 20px;
    margin: 0px 40px 100px 40px;
  }
  .popup__question {
    font-size: 16px;
    line-height: 22px;
  }
  .popup__questionAdditional {
    font-size: 16px;
    line-height: 22px;
  }
  .button__block {
    display: flex;
    padding: 0;
  }

  .buttonBack {
    margin: 16px 30px 54px 40px;
    max-width: 48px;
    height: 20px;
    font-size: 16px;
    line-height: 19px;
  }
  .buttonNext {
    max-width: 200px;
    height: 48px;
    margin: 0px 482px 40px 0px;
  }
  .buttonNext__description {
    width: 66px;
    height: 20px;
    font-size: 16px;
    line-height: 19px;
  }

  .icon__close {
    width: 17.36px;
    /* left: 757px;
bottom: 87.82px; */
    top: 35px;
    left: 757px;
    position: absolute;
  }
}

@media all and (max-width: 1023px) {
  .popupQuiz {
    max-width: 800px;
    height: 520px;
  }

  .popup__step {
    width: 720px;
    height: 20px;
    font-weight: 500;
    font-size: 15px;
    line-height: 22px;
    margin: 40px 611px 40px 40px;
  }
  .popup__questions_block {
    margin: 0px 40px 100px 40px;
    max-width: 720px;
    height: 20px;
    font-weight: 500;
    font-size: 15px;
    line-height: 22px;
  }
  .popup__question {
    font-size: 15px;
    line-height: 22px;
    font-weight: 500;
  }
  .popup__questionAdditional {
    font-size: 15px;
    line-height: 22px;
    font-weight: 500;
  }
  .button__block {
    display: flex;
    padding: 0;
  }

  .buttonBack {
    margin: 16px 30px 53px 40px;
    max-width: 48px;
    height: 20px;
    font-size: 15px;
    line-height: 18px;
  }
  .buttonNext {
    max-width: 200px;
    height: 46px;
    margin: 0px 482px 40px 0px;
  }
  .buttonNext__description {
    margin: auto;
    max-width: 66px;
    height: 20px;
    font-weight: 500;
    font-size: 15px;
    line-height: 18px;
  }

  .icon__close {
    width: 17.36px;
    top: 35px;
    left: 757px;
    position: absolute;
  }
}

@media all and (max-width: 767px) {
  .popupQuiz {
    max-width: 580px;
    height: 520px;
  }

  .popup__step {
    max-width: 144px;
    height: 30px;
    font-weight: 600;
    font-size: 23px;
    line-height: 30px;
    margin: 40px 396px 40px 40px;
  }

  .popup__questions_block {
    margin: 0px 40px 100px 40px;
    max-width: 500px;
    height: 20px;
    font-weight: 500;
    font-size: 15px;
    line-height: 19px;
  }
  .popup__question {
    font-weight: 500;
    font-size: 15px;
    line-height: 19px;
  }
  .popup__questionAdditional {
    font-weight: 500;
    font-size: 15px;
    line-height: 19px;
  }
  .button__block {
    display: flex;
    padding: 0;
  }

  .buttonBack {
    margin: 16px 30px 53px 40px;
    max-width: 48px;
    height: 20px;
    font-size: 15px;
    line-height: 18px;
  }
  .buttonNext {
    margin: 0px 262px 40px 0px;
    max-width: 200px;
    height: 46px;
  }
  .buttonNext__description {
    margin: auto;
    max-width: 66px;
    height: 20px;
    font-weight: 500;
    font-size: 15px;
    line-height: 18px;
  }

  .icon__close {
    width: 20px;
    height: 20px;
    top: 47px;
    left: 537px;
    position: absolute;
  }
}

@media all and (max-width: 455px) {
  .popupQuiz {
    max-width: 290px;
    height: 520px;
  }

  .popup__step {
    max-width: 100px;
    height: 21px;
    font-weight: 600;
    font-size: 16px;
    line-height: 21px;
    margin: 15px 175px 30px 15px;
  }
  .popup__questions_block {
    margin: 0px 15px 100px 15px;
    max-width: 260px;
    height: 20px;
    font-weight: 500;
    font-size: 13px;
    line-height: 16px;
  }
  .popup__question {
    font-weight: 500;
    font-size: 13px;
    line-height: 16px;
  }
  .popup__questionAdditional {
    font-weight: 500;
    font-size: 13px;
    line-height: 16px;
  }
  .button__block {
    display: flex;
    padding: 0;
  }

  .buttonBack {
    margin: 16px 15px 27px 15px;
    max-width: 39px;
    height: 16px;
    font-size: 13px;
    line-height: 16px;
  }
  .buttonNext {
    margin: 0px 15px 15px 0px;
    max-width: 206px;
    height: 40px;
  }
  .buttonNext__description {
    max-width: 42px;
    height: 16px;
    font-weight: 500;
    font-size: 13px;
    line-height: 16px;
    margin: auto;
  }

  .icon__close {
    width: 20px;
    height: 20px;
    top: 23px;
    left: 257px;
    position: absolute;
  }
}
</style>
