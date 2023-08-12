<script setup>
function calcularIMC() {
  const card = document.querySelectorAll(".card");
  const baixo = document.querySelector(".baixo");
  const normal = document.querySelector(".normal");
  const sobrePeso = document.querySelector(".sobrePeso");
  const obsidade = document.querySelector(".obsidade");
  const altura = document.getElementById("altura");
  const peso = document.getElementById("peso");
  const res = document.querySelector("#res");
  const resultado = peso.value / (altura.value * altura.value);
  res.innerHTML = `Seu IMC atual é de  ${resultado.toFixed(2)}`;

  if (altura.value <= 0 && peso.value <= 0) {
    altura.style = " border: 2px solid #be201c;";
    peso.style = "border: 2px solid #be201c;";
    res.style = "color: #be201c";
    res.innerHTML = `Informe sua altura e seu peso primeiro.`;
  } else {
    altura.style = "";
    peso.style = "";
    res.style = "";
  }

  function colorTable() {
    card.forEach((item) => {
      item.classList.remove("yellow", "green", "orange", "red");
    });
    if (resultado < 18.5) {
      baixo.classList.add("yellow");
    } else if (resultado <= 24.99) {
      normal.classList.add("green");
    } else if (resultado <= 30) {
      sobrePeso.classList.add("orange");
    } else if (resultado <= 40) {
      obsidade.classList.add("red");
    } else {
    }
  }
  colorTable();
}
</script>

<template>
  <div class="container">
    <div class="right">
      <p class="sobreIMC">
        O IMC é reconhecido como padrão internacional para avaliar o grau de
        sobrepeso e obesidade. É calculado dividindo o peso (em kg) pela altura
        ao quadrado (em metros).
        <span>IMC = Peso ÷ (Altura x Altura)</span>
        Exemplo de como calcular o IMC:
        <span>IMC = 80 kg ÷ (1,80 m x 1,80 m) = 24,69 kg/m2 (Peso ideal)</span>
        Utilize a calculadora abaixo para fazer o seu cálculo:
      </p>
      <div class="inputIMC">
        <label class="labelIMC" for="altura"
          >Infome sua altura (metro . cm)</label
        >
        <input
          class="input"
          type="number"
          id="altura"
          name="altura"
          placeholder="1.80"
        />
      </div>
      <div class="inputIMC">
        <label class="labelIMC" for="peso">Informe seu peso (kg)</label>
        <input
          class="input"
          type="number"
          id="peso"
          name="peso"
          placeholder="59,00"
        />
      </div>
      <div>
        <button class="btn" @click="calcularIMC()">Calcular</button>
      </div>

      <div id="res"></div>
    </div>
    <div class="left">
      <div class="card baixo">
        <p class="valor">Menor que 18,5</p>
        <p class="class">Peso baixo</p>
      </div>
      <div class="card normal">
        <p class="valor">De 18,5 a 24,99</p>
        <p class="class">Peso normal</p>
      </div>
      <div class="card sobrePeso">
        <p class="valor">De 25 a 29,99</p>
        <p class="class">Sobrepeso</p>
      </div>
      <div class="card obsidade">
        <p class="valor">Maior que 30</p>
        <p class="class">Obsidade</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  place-content: center;
  height: 100vh;
  width: 100vw;
}
.right {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.sobreIMC {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-items: center;
  margin: 0 25px;
  padding: 5px;
  font-size: 18px;
}
.sobreIMC span {
  margin: 10px 0;
  color: green;
  font-weight: bold;
  text-align: center;
}
.card {
  background-color: #777;
  text-align: center;
  padding: 10px;
  border-radius: 8px;
  color: #000;
  font-size: 18px;
  margin-top: 10px;
  width: 500px;
}
.yellow {
  background-color: #e4e400;
}
.green {
  background-color: #7cfc00;
}
.orange {
  background-color: #ffa500;
}
.red {
  background-color: #be201c;
}
#res {
  font-size: 30px;
  margin-top: 20px;
  padding: 20px;
  color: green;
  text-align: center;
}
.inputIMC {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 5px;
}
.labelIMC {
  font-size: 16px;
  color: green;
  font-weight: bold;
}
.input {
  background-color: #fff;
  font-size: 18px;
  width: 300px;
  height: 40px;
  padding: 10px;
  border: 1px solid #000;
  border-radius: 5px;
}
.input::placeholder {
  font-size: 18px;
}
.input:focus {
  color: green;
  background-color: transparent;
  outline-color: green;
  transition: 0.1s;
  transition-property: box-shadow;
}
.btn {
  background-color: transparent;
  font-size: 18px;
  padding: 10px 30px;
  cursor: pointer;
  border: 2px solid green;
  border-radius: 8px;
  transition: 0.5s all;
  margin-top: 10px;
}
.btn:hover {
  background-color: green;
  color: #fff;
}
.btn:active {
  transform: scale(0.9);
}
@media screen and (max-width: 768px) {
  .container {
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 100%;
    padding: 5px;
  }
  .sobreIMC {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-items: center;
  margin: 0 ;
  padding: 0;
  font-size: 16px;
}
.card {
  padding: 10px;
  font-size: 16px;
  width: 100%;
}
.left {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 10px;
}
#res {
  font-size: 25px;
  margin-top: 10px;
  padding: 10px;
}
}
</style>
