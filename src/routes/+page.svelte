<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	let inputValue = 0;
	let selectedUnitValue = 'lb';
	let convertedWeightText = ''

        function convertWeight() {
            const weightInput = inputValue
            const selectedUnit = selectedUnitValue
            let convertedWeight;

            switch (selectedUnit) {
                case "lb":
                    convertedWeight = weightInput;
                    break;
                case "mt":
                    convertedWeight = weightInput * 1000;
                    break;
                case "ST":
                    convertedWeight = weightInput * 2000;
                    break;
                case "LT":
                    convertedWeight = weightInput * 2240;
                    break;
                case "oz":
                    convertedWeight = weightInput * 16;
                    break;
                case "µg":
                    convertedWeight = weightInput / 1000000;
                    break;
                case "kg":
                    convertedWeight = weightInput * 2.20462;
                    break;
                default:
                    convertedWeight = "Invalid unit";
            }
						convertedWeightText = `Converted weight: ${convertedWeight.toFixed(2)} ${selectedUnit}`

            
        }
    </script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>




 
   


    <h1>Weight Conversion Calculator</h1>
    <form >
        <label for="weight">Enter weight:</label>
        <input bind:value={inputValue} type="number" id="weight" name="weight" required>
        <select id="unit" name="unit" bind:value={selectedUnitValue}>
            <option value="lb">Pounds (lb)</option>
            <option value="mt">Metric Ton (mt)</option>
            <option value="ST">Short Ton (ST)</option>
            <option value="LT">Long Tons (LT)</option>
            <option value="oz">Ounces (oz)</option>
            <option value="µg">Micrograms (µg)</option>
            <option value="kg">Kilograms (kg)</option>
        </select>
        <button on:click={convertWeight}  >Convert</button>
    </form>
    <p id="result">
			{convertedWeightText}
		</p>


