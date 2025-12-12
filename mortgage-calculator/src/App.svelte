<script>
  let loanAmount = 250000;
  let interestRate = 3.5;
  let loanTerm = 30;

  $: monthlyPayment = (
    (loanAmount * (interestRate / 100 / 12)) /
    (1 - Math.pow(1 + interestRate / 100 / 12, -loanTerm * 12))
  ).toFixed(2);
</script>

<main>
  <h1>Mortgage Calculator</h1>

  <div class="form-group">
    <label for="loanAmount">Loan Amount</label>
    <input type="number" id="loanAmount" min="0" bind:value={loanAmount} />
  </div>

  <div class="form-group">
    <label for="interestRate">Interest Rate: {interestRate}%</label>
    <input type="range" id="interestRate" min="1" max="10" step="0.1" bind:value={interestRate} />
  </div>

  <div class="form-group">
    <label for="loanTerm">Loan Term: {loanTerm} years</label>
    <input type="range" id="loanTerm" min="5" max="40" bind:value={loanTerm} />
  </div>

  <h2>Monthly Payment: ${monthlyPayment}</h2>
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    background-image: url('https://nanobanana.io/images/ff00ff/ff0000/256/256');
    background-size: cover;
    background-position: center;
    padding: 20px;
  }

  h1 {
    font-size: 3em;
    text-shadow: 0 0 10px #ff0000, 0 0 20px #ff0000;
  }

  .form-group {
    margin-bottom: 20px;
    width: 100%;
    max-width: 400px;
  }

  label {
    display: block;
    margin-bottom: 5px;
    font-size: 1.2em;
    text-shadow: 0 0 5px #ff0000;
  }

  input[type="number"],
  input[type="range"] {
    width: 100%;
    padding: 10px;
    border: 1px solid #ff0000;
    background-color: rgba(0, 0, 0, 0.5);
    color: #ff0000;
    border-radius: 5px;
  }

  input[type="range"] {
    -webkit-appearance: none;
    appearance: none;
    height: 10px;
    border-radius: 5px;
    background: #ff0000;
    outline: none;
    opacity: 0.7;
    -webkit-transition: .2s;
    transition: opacity .2s;
  }

  input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 25px;
    height: 25px;
    border-radius: 50%;
    background: #ff0000;
    cursor: pointer;
    box-shadow: 0 0 10px #ff0000;
  }

  input[type="range"]::-moz-range-thumb {
    width: 25px;
    height: 25px;
    border-radius: 50%;
    background: #ff0000;
    cursor: pointer;
    box-shadow: 0 0 10px #ff0000;
  }

  h2 {
    font-size: 2em;
    text-shadow: 0 0 10px #ff0000, 0 0 20px #ff0000;
  }
</style>
