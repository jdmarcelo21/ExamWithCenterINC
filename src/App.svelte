<script>
//	let name = '';
let answer = '0';
  let operator = '';
  let arguement1 = '';

  const handleClick = (event) => {
    const value = event.target.dataset.value;

    if (value === 'C') {
      answer = '0';
      operator = '';
      arguement1 = '';
    }
	else if (value === '+' || value === '-' || value === '*' || value === '/') {
      if (answer !== '0') {
        operator = value;
        arguement1 = answer;
        answer = '0';
      }
    }
	else if (value === '=') {
      if (operator && arguement1) {
        answer = calculateanswer();
        operator = '';
        arguement1 = '';
      }
    }  else {
      if (answer === '0') {
        answer = value;
      } else {
        answer += value;
      }
    }
  };

  const calculateanswer = () => {
    const num1 = parseFloat(arguement1);
    const num2 = parseFloat(answer);

    switch (operator) {
      case '+':
        return (num1 + num2).toString();
      case '-':
        return (num1 - num2).toString();
      case '*':
        return (num1 * num2).toString();
      case '/':
        return (num1 / num2).toString();
      default:
        return answer;
    }
  };


</script>

<main>
	<h1>Calculator</h1>
	<div class="border">
	<div class="calculator">
		<h4 class="answer1">{answer}</h4>
	  <div class="buttons">
		<button on:click={handleClick} data-value="7">7</button>
		<button on:click={handleClick} data-value="8">8</button>
		<button on:click={handleClick} data-value="9">9</button>
		<button class="button2" on:click={handleClick} data-value="C">C</button>

		<button on:click={handleClick} data-value="4">4</button>
		<button on:click={handleClick} data-value="5">5</button>
		<button on:click={handleClick} data-value="6">6</button>
		<button on:click={handleClick} data-value="+">+</button>

		<button on:click={handleClick} data-value="1">1</button>
		<button on:click={handleClick} data-value="2">2</button>
		<button on:click={handleClick} data-value="3">3</button>
		<button on:click={handleClick} data-value="-">-</button>

		<button on:click={handleClick} data-value="0">0</button>
		<button on:click={handleClick} data-value=".">.</button>
		<button on:click={handleClick} data-value="/">/</button>
		<button on:click={handleClick} data-value="*">*</button>

			
	  </div>
	</div>
	<div>
		<button class="button1" on:click={handleClick} data-value="="> = </button>
		</div>
	</div>
</main>

<style>
	/* main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}  */

	main {
		text-align: center;
		padding: 1em;
		max-width: 230px;
		margin: 0 auto;
	}

	.calculator {

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
	
  }


  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 0.9rem;
	
  }

  button {
    padding: 0.8rem;
    font-size: 1rem;
    background-color: #ccc;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  .answer1{
	border-style: groove;
	text-align: right;
	width: 80%;
	font-size: 18px;

  }

  .button1{
	margin-top: 5%;
	width: 83%;
	background-color:bisque;
	font-size: 18px;
  }

  .button2{
	background-color: #4bccff;
  }

  .border{
	border-style: groove;
	font-weight: bold;
  }

</style>