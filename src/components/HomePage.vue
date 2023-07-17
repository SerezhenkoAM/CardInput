<template>
  <div class="home">
    <div class="home__card">
      <Default_card v-if="state_1" :card="card" class="home__default-card" />
      <Sberbank_card v-if="state_2" :card="card" class="home__default-card " />
      <Alfa_card v-if="state_3" :card="card" class="home__default-card " />
    </div>
    <div class="home__inputs">
      <p>Номер карты</p>
      <input type="text" class="home__input" maxlength="16" v-model="card.number" @input="image_check">
      <p>Владелец карты</p>
      <input type="text" class="home__input" maxlength="30" v-model="card.person">
      <p>Срок эксплуатации</p>
      <div class="home__input_date">
        <input type="text" maxlength="2" placeholder="Месяц" v-model="card.month" @input="validation">
        <input type="text" maxlength="2" placeholder="Год" v-model="card.year" @input="validation">
        <input type="text" maxlength="3" placeholder="CVV" @input="validation" />
      </div>
    </div>
    <button class="home__button">Подтвердить оплату</button>
  </div>
</template>
<script>
import Sberbank_card from '../ui/card/Sberbank/Sberbank_card.vue'
import Default_card from '../ui/card/Default/Default_card.vue'
import Alfa_card from '../ui/card/Alfa/Alfa_card.vue'
export default {
  name: 'HomePage',
  components: {
    Sberbank_card,
    Default_card,
    Alfa_card
  },
  data() {
    return {
      card: {
        person: '',
        number: '',
        month: '',
        year: '',
        img: ''
      },
      state: 0,
      state_1: true,
      state_2: false,
      state_3: false,

    }
  },
  methods: {
    validation() {
      this.card.number = this.card.number.replace(/\D/g, '');
      this.card.month = this.card.month.replace(/\D/g, '');
      this.card.year = this.card.year.replace(/\D/g, '');
    },
    image_check() {
      this.card.number = this.card.number.replace(/\D/g, '');
      this.state = this.card.number.slice(0, 4)

      if (this.state > 550000 && this.state < 600000) {
        this.card.img = '/img/mastercard.171388b2.png'
      }
      else if (this.state < 550000) {
        this.card.img = '/img/visa.cd1c208d.png'
      } else {
        this.card.img = ''
      }


      if (this.state > 5000) {
        this.state_2 = true
        this.state_3 = false
        this.state_1 = false

      }
      if (this.state < 4999 && this.state > 2000) {
        this.state_2 = false
        this.state_3 = true
        this.state_1 = false
      }
      if (this.state == '') {
        this.state_1 = true;
        this.state_2 = false;
        this.state_3 = false;
      }
      if (this.state < 1999) {
        this.state_1 = true;
        this.state_2 = false;
        this.state_3 = false;
      }
    }
  }
}
</script>

<style scoped lang="less">
@keyframes opac {
  from {
    opacity: 0;
    transform: translateX(-40px)
  }
  to {
    opacity: 1
  }
}

@import url('https://fonts.googleapis.com/css2?family=Heebo:wght@300;400&family=Jost:ital,wght@0,300;0,400;0,500;1,400&family=Manrope&family=Poppins&display=swap');
@Heebo: 'Heebo';
@Poppins: 'Poppins';
@Jost: 'Jost';

.home {
  width: 40vw;
  padding: 30px 40px;
  box-shadow: 0px 0px 100px 1px rgba(34, 60, 80, 0.2);
  border-radius: 5px;
  margin: 0 auto;
  background-color: #fff;
  position: relative;
  margin-top: 200px;
  padding-top: 110px;

  @media screen and (max-width: 1000px) {
    width: 70%;
    margin-top: 130px;
  }

  &__default-card {
    animation: opac 1s;
  }

  &__card {
    position: absolute;
    top: -150px;
    left: 50%;
    transform: translateX(-50%);

    @media screen and (max-width: 600px) {
      top: -110px;
    }
  }

  &__inputs {
    p {
      color: #758597;
      font-family: @Jost;
      margin: 10px 0;
    }

    input {
      color: #15181b;
      border: 1px solid #758597;
      padding: 10px 10px;
      border-radius: 5px;
      width: 98%;
      font-size: 17px;
      margin-bottom: 20px;
      outline: none;
    }
  }

  &__input_date {
    display: flex;
    width: 100%;
    justify-content: space-between;
    gap: 30px
  }

  &__button {
    width: 100%;
    padding: 10px 0;
    background-color: #2790d8;
    color: white;
    font-family: @Jost;
    font-size: 20px;
    outline: none;
    border: none;
    border-radius: 5px;
    margin-top: 20px;
  }
}
</style>
