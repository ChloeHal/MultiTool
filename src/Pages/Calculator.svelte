<script>
    let firstNumber = 0;
let secondNumber = 0;
let operation = '';
let result = 0;
const resultElement = document.querySelector('.result');
function handleClick(value) {
  if (value === 'clear') {
    firstNumber = 0;
    secondNumber = 0;
    operation = '';
    result = 0;
  } else if (value === '+' || value === '-' || value === '*' || value === '/') {
    operation = value;
  } else if (operation === '') {
    if (!isNaN(value)) {
      firstNumber = parseFloat(firstNumber + value);
      result = firstNumber;
    }
  } else {
    if (!isNaN(value)) {
      secondNumber = parseFloat(secondNumber + value);
      result = eval(firstNumber + operation + secondNumber);
    }
  }
      
      resultElement.textContent = result;
    }
  </script>
  
  <div class="calculator">
    <div class="result my-4">{result}</div>
    <div class="grid grid-cols-4 gap-2 mb-4">
      <button class="btn btn-circle" on:click={() => handleClick('7')}>7</button>
      <button class="btn btn-circle" on:click={() => handleClick('8')}>8</button>
      <button class="btn btn-circle" on:click={() => handleClick('9')}>9</button>
      <button class="btn btn-circle btn-outline" on:click={() => handleClick('/')}>/</button>
      <button class="btn btn-circle" on:click={() => handleClick('4')}>4</button>
      <button class="btn btn-circle" on:click={() => handleClick('5')}>5</button>
      <button class="btn btn-circle" on:click={() => handleClick('6')}>6</button>
      <button class="btn btn-circle btn-outline" on:click={() => handleClick('*')}>*</button>
      <button class="btn btn-circle" on:click={() => handleClick('1')}>1</button>
      <button class="btn btn-circle" on:click={() => handleClick('2')}>2</button>
      <button class="btn btn-circle" on:click={() => handleClick('3')}>3</button>
      <button class="btn btn-circle btn-outline" on:click={() => handleClick('-')}>-</button>
      <button class="btn btn-circle" on:click={() => handleClick('0')}>0</button>
      <button class="btn btn-circle" on:click={() => handleClick('00')}>00</button>
      <button class="btn btn-circle btn-outline" on:click={() => handleClick('clear')}>C</button>
      <button class="btn btn-circle btn-outline" on:click={() => handleClick('+')}>+</button>
    </div>
  </div>