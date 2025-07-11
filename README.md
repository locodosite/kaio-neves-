# kaio-neves
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Simulador de Investimentos - Feito por Kaio</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      max-width: 600px;
      margin: 30px auto;
      padding: 20px;
      border-radius: 10px;
      background: white;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h1 {
      text-align: center;
      color: #2c3e50;
    }
    label {
      display: block;
      margin-top: 10px;
    }
    input {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      width: 100%;
      padding: 10px;
      background-color: #27ae60;
      color: white;
      border: none;
      border-radius: 4px;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background-color: #2ecc71;
    }
    #resultado {
      text-align: center;
      margin-top: 20px;
      font-size: 20px;
      color: #34495e;
    }
    canvas {
      margin-top: 30px;
    }
    footer {
      margin-top: 40px;
      text-align: center;
      font-size: 14px;
      color: #999;
    }
  </style>
</head>
<body>
  <h1>Simulador de Investimento</h1>

  <label>Valor investido (R$):</label>
  <input type="number" id="valor" placeholder="Ex: 1000">

  <label>Tempo (meses):</label>
  <input type="number" id="tempo" placeholder="Ex: 12">

  <label>Juros ao mês (%):</label>
  <input type="number" id="juros" placeholder="Ex: 1">

  <button onclick="calcular()">Calcular</button>

  <div id="resultado"></div>
  <canvas id="grafico" height="100"></canvas>

  <footer>
    Feito com 💻 por <strong>Kaio Neves dos Santos</strong>
  </footer>

  <script>
    function calcular() {
      const valor = parseFloat(document.getElementById("valor").value);
      const tempo = parseInt(document.getElementById("tempo").value);
      const juros = parseFloat(document.getElementById("juros").value) / 100;

      if (isNaN(valor) || isNaN(tempo) || isNaN(juros)) {
        alert("Preencha todos os campos corretamente.");
        return;
      }

      const valores = [];
      const meses = [];

      for (let i = 0; i <= tempo; i++) {
        const montante = valor * Math.pow(1 + juros, i);
        valores.push(montante.toFixed(2));
        meses.push(i + "º");
      }

      document.getElementById("resultado").innerText =
        "Total após " + tempo + " meses: R$ " + valores[valores.length - 1];

      gerarGrafico(meses, valores);
    }

    let grafico;

    function gerarGrafico(labels, data) {
      const ctx = document.getElementById("grafico").getContext("2d");

      if (grafico) {
        grafic
