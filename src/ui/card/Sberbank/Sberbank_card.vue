<template>
  <div class="sber">

    <div class="sber__header">
      <img src="../../../assets/sberbank.svg" alt="" class="sber__logo">
      <p class="sber__bank-name">СБЕРБАНК</p> 
    </div>
    <div class="sber__wrapp-number">
      <img src="../../../assets/chip.png" alt="" class="sber__chipset">
      <div class="">
        <p v-for="item in card.number" :key="item" class="sber__number">
          {{ item }}
        </p>
      </div>
    </div>
    <div class="sber__wrapp-date">
      <div>Пользователь</div>
      <div class="sber__date-text">
        <div>МЕСЯЦ/ГОД</div>
        <div class="sber__date">
          <p>{{ card.month }}</p>
          <p>/</p>
          <p>{{ card.year }}</p>
        </div>
      </div>
    </div>

    <!-- ing absolute right 0 bottom 0 -->
    <div class="sber__wrapp-name">
      <div class="sber__name">
        <div>{{ card.person }}</div>
      </div>

      <div class="sber__type-pay">
        <img src="../../../assets/mastercard.png" alt="">
      </div>
    </div>


  </div>
</template>

<script>


export default   {
  name: 'sber_card',
  components: {
  },
  props: {
    card: Object,
    image: String
  },
  data() {
    return {
    }
  },
  methods: {
  }
}
</script>

<style scoped lang="less">
@keyframes trans {
  from {
    opacity: 0;
    transform: translateY(15px)
  }
  to {
    opacity: 1
  }
}

@import url('https://fonts.googleapis.com/css2?family=Public+Sans:wght@300;400&display=swap');
@Sans: 'Public Sans';

* {
  margin: 0;
  padding: 0;
  color: white;
}

.sber {
  border-radius: 25px;
  padding: 20px 20px;
  width: 400px;

  border-radius: 25px;
  padding: 20px 20px;
  width: 400px;
  background: rgba(113, 204, 28, 0.9);
  font-family: @Sans;

  &__header {
    display: flex;
    align-items: center;

    img {
      width: 30px;
      height: 30px;
    }

    p {
      font-size: 20px;
      text-decoration: underline;
      letter-spacing: 1px;

    }

  }

  @media screen and (max-width: 600px) {
    width: 65vw;
    padding: 15px 15px;
  }


  &__header {
    display: flex;
    align-items: center;

    img {
      width: 30px;
      height: 30px;
      margin-right: 5px;

      @media screen and (max-width: 600px) {
        width: 25px;
        height: 25px;
      }
    }

    p {
      margin-left: 5px;
      font-size: 30px;
      font-weight: 400;
      letter-spacing: 1px;

      @media screen and (max-width: 600px) {
        font-size: 17px;
        margin-left: 2px;
      }
    }

  }

  &__chipset {
    height: 40px;
    width: 43px;
    margin-left: 10px;
  }

  &__wrapp-number {
    margin-top: 45px;

    @media screen and (max-width: 600px) {
      margin-top: 19px;    
    }

    div {
      display: flex;
      margin-left: 12px;
      font-size: 25px;
      min-height: 30px;

      @media screen and (max-width: 600px) {
        font-size: 16px;
        min-height: 20px;
      }
    

      p {
        font-family: @Sans;
        letter-spacing: 2px;
        animation: trans .5s;
      }

      p:nth-child(4n) {
        margin-right: 12px;
      }

    }
  }

  &__wrapp-date {
    display: flex;
    justify-content: center;
    margin-top: 5px;

    &>div:nth-child(1) {
      align-self: flex-end;
      font-size: 10px;
    }
  }

  &__date-text {
    align-self: flex-end;

    &>div:nth-child(1) {
      font-size: 10px;
      margin: 2px;

      @media screen and (max-width: 600px) {
        font-size: 9px;
      }
    }
  }

  &__date {
    display: flex;
    justify-content: center;
    height: 19px;
    font-size: 18px;
    @media screen and (max-width: 600px) {
      font-size: 14px;
    }
  }

  &__wrapp-name {
    margin-left: 12px;
  }

  &__name {
    font-size: 17px;
    min-height: 20px;
          
    @media screen and (max-width: 600px) {
      font-size: 15px;
    }
  }


  &__type-pay {
    position: absolute;
    right: 0;
    bottom: 0;
    margin-right: 20px;
    margin-bottom: 15px;

    img {
      width: 70px;
      height: 45px;

      @media screen and (max-width: 600px) {
        width: 50px;
        height: 30px;
      }
    }
  }




}</style>
