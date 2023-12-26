<script lang="ts">
	const numbers = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "0", "."];
	const operators = ["/", "*", "+", "-", "="];

	let selectedOperator = "";
	let display = "";

	let num1 = "";
	let num2 = "";
	let isDisplayingResults = false;

	const handleSelectedOperator = (operator: string) => {
		if (!num1) return;
		if (operator === "=") {
			if (!num2) return;
			const n1 = parseFloat(num1);
			const n2 = parseFloat(num2);

			let result = "";

			switch (selectedOperator) {
				case "/":
					if (selectedOperator === "/" && n2 === 0) {
						display = "Error";
						return;
					}
					result = (n1 / n2).toFixed(2);
					break;
				case "*":
					result = (n1 * n2).toFixed(2);
					break;
				case "+":
					result = (n1 + n2).toFixed(2);
					break;
				case "-":
					result = (n1 - n2).toFixed(2);
					break;
			}
			display = result;
		}
		selectedOperator = operator;
		isDisplayingResults = true;
	};

	const handleSelectedNumber = (number: string) => {
		if (display === "" && number === "0") return;
		if (number === "." && display.includes(".")) return;

		if (!selectedOperator) {
			if (display === "" && number === ".") {
				num1 = "0.";
				return (display = num1);
			}
			num1 += number;
			display = num1;
		} else {
			if (display === "" && number === ".") {
				num2 = "0.";
				return (display = num2);
			}
			num2 += number;
			display = num2;
		}
	};

	const clearDisplay = () => {
		selectedOperator = "";
		display = "";
		num1 = "";
		num2 = "";
		isDisplayingResults = false;
	};
</script>

<main>
	<div class="calculator">
		<div class="result">
			{display}
		</div>
		<div class="digits">
			<div class="numbers">
				<button class="btn btn-xlg" on:click={() => clearDisplay()}> C </button>
				{#each numbers as number (number)}
					<button
						class={`btn ${number === "0" ? "btn-lg" : null}`}
						on:click={() => handleSelectedNumber(number)}>{number}</button
					>
				{/each}
			</div>
			<div class="operations">
				{#each operators as operator (operator)}
					<button
						class={`btn btn-orange ${
							operator === selectedOperator ? "btn-silver" : "btn-orange"
						}`}
						on:click={() => handleSelectedOperator(operator)}
					>
						{operator}
					</button>
				{/each}
			</div>
		</div>
	</div>
</main>

<style>
	main {
		width: 100vw;
		height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: rgb(20, 20, 20);
	}
	.calculator {
		background-color: rgb(28, 28, 28);
		width: 240px;
		padding: 15px;
		border-radius: 10px;
	}
	.digits {
		display: flex;
	}
	.operations {
		display: flex;
		flex-direction: column;
	}
	.numbers {
		display: flex;
		flex-wrap: wrap;
		width: 200px;
	}
	.btn {
		width: 50px;
		height: 50px;
		border-radius: 100px;
		background-color: rgb(114, 113, 113);
		font-size: 20px;
		font-weight: bold;
		color: white;
		margin: 5px;
		border: none;
	}
	.btn-lg {
		width: 110px;
	}
	.btn-orange {
		background-color: orange;
	}
	.btn-silver {
		background-color: silver;
	}
	.btn-xlg {
		width: 170px;
	}
	.result {
		height: 60px;
		color: white;
		font-size: 50px;
		display: flex;
		flex-direction: row-reverse;
		margin-right: 10px;
	}
</style>
