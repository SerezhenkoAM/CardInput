<template>
  <div class="default">
    <div class="default__header">
      <p class="default__bank-name">Банк</p>
    </div>
    <div class="default__wrapp-number">
      <img src="../../../assets/chip_black.png" alt="" class="default__chipset">
      <div class="">
        <p v-for="item in card.number" :key="item" class="default__number">
          {{ item }}
        </p>
      </div>
    </div>
    <div class="default__wrapp-date">
      <div>Пользователь</div>
      <div class="default__date-text">
        <div>МЕСЯЦ/ГОД</div>
        <div class="default__date">
          <p>{{ card.month }}</p>
          <p>/</p>
          <p>{{ card.year }}</p>
        </div>
      </div>
    </div>
    <div class="default__wrapp-name">
      <div class="default__name">
        <div>{{ card.person }}</div>
      </div>
      <div class="default__type-pay">
        <img src="../../../assets/mastercard.png" alt="">
      </div>
    </div>


  </div>
</template>

<script>
export default {
  name: 'default_card',
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
  color: black;
}

.default {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-radius: 25px;
  border: 1px solid rgba(0, 0, 0, 0.5);
  box-shadow: 0px 0px 100px 1px rgba(0, 0, 0, 0.2);
  margin: 0 auto;
  padding: 20px 20px;
  width: 400px;

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
    }

    p {
      margin-left: 12px;
      font-size: 30px;
      font-weight: 400;
      letter-spacing: 1px;

      @media screen and (max-width: 600px) {
        font-size: 25px;
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
