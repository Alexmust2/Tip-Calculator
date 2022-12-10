<template>
  <div class="container">
    <div class="calculator">
      <div class="bill_container">
        <h3 class="bill">Счет</h3>
        <input type="number" maxlength="6" name="bill" v-model="bill" title="Максимальная сумма 1.000.000₽">
        <h4 v-if="this.bill > 1000000" style="color: red; margin-top: 5px; margin-left: 20px;">Слишком большая сумма</h4>
      </div>
      <h3 class="select">Выберите процент чаевых</h3>
      <div class="buttons">
        <TipButton @click="getResult(5)">5%</TipButton>
        <TipButton @click="getResult(10)">10%</TipButton>
        <TipButton @click="getResult(15)">15%</TipButton>
        <TipButton @click="getResult(25)">25%</TipButton>
        <TipButton @click="getResult(50)">50%</TipButton>
        <TipButton @click="getResult(this.customTip)"><input type="number" class="custom" placeholder="Custom" v-model="customTip"></TipButton>
      </div>
    </div>
    <div class="result_container">
      <div class="result">
        <span>Сумма</span>
        <span style="margin-left: 125px; font-size: 20px;">{{result}}₽</span>
      </div>
      <span @click="clear" class="clear">Сбросить</span>
    </div>
  </div>
</template>

<script>
import TipButton from '@/components/UI/TipButton.vue'
  export default {
    components: {
      TipButton,
    },
    data() {
      return {
        bill: "",
        result: "0",
        customTip: "",
      }
    },
    methods: {
      getResult(value) {
        this.result = this.bill * value / 100
      },
      clear() {
        this.result = "0";
        this.bill = ""
      }
    }
  }
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@500&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Montserrat', sans-serif;
  overflow: none
}

.custom {
  width:60px;
  text-align: center;
  outline:0;
  border: none;
  background: none;
  font-size: 18px;
  font-weight: 200;
}

.custom::placeholder {
  font-size: 14px;
}

.result {
  display: flex;
  span {
    font-weight: 200;
    line-height: 28px;
    font-size: 14px;
    word-wrap: no-wrap;
  }
}

.container {
  background: linear-gradient(50deg, rgba(255, 255, 255, 0.6) 12%,rgba(255, 255, 255, 0.5) 77%);

  max-width: 40rem;
  height: 25rem;

  border-radius: 15px;
  box-shadow: 13px 15px 0px 0px rgba(0, 0, 0, 0.3);

  margin: auto;
  margin-top: 15rem;
  padding: 15px;

  display: flex;
  justify-content: center;
}

.bill_container {
  display: flex;
  flex-direction: column;
  justify-content: center;

  width: 20rem;
  height: 10rem;
  .bill {
    font-size: 18px;
    font-weight: 200;
    
    margin-left: 20px;
  }
  input {
    border: none;
    border-bottom: 1px solid black;
    outline:0;
    height: 20px;
    width: 82%;

    background: none;

    margin-top: 15px;
    margin-left: 20px;
    padding: 15px;

    font-size: 18px;

    overflow: none;
  }
}

  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

.select {
  margin-bottom: 5px;
  margin-left: 20px;

  font-weight: 200;
}

.buttons {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  
  width: 300px;
}

.calculator {
  width: 22.2rem;
}

.result_container {
  width: 20rem;
  height: 90%;

  display: flex;
  flex-direction: column;

  margin-top: 15px;
  margin-left: auto;
  padding: 15px;

  background: rgba(114, 196, 112, 0.61);
  border-radius: 15px;
}

.clear {
  width: 250px;
  height: 50px;

  align-self: center;
  text-align: center;

  line-height: 50px;
  font-size: 14px;

  position: fixed;

  background-color: rgba(0, 128, 128, 0.493);
  border-radius: 5px;

  margin-top: 250px;

  cursor: pointer;
}

body {
  background-color: rgba(64, 61, 241, 0.35);
}

</style>
