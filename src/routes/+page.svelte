<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';

	const conversionTable = {
		lb: {
			kg: 0.453592,
			oz: 16,
			LT: 0.000453592,
			ST: 0.0005,
			mt: 0.000453592,
			µg: 453592370
			// Add more conversions here
		},
		kg: {
			lb: 2.20462,
			oz: 35.274,
			LT: 0.001,
			ST: 0.00110231,
			mt: 0.001,
			µg: 1000000000
			// Add more conversions here
		},
		oz: {
			lb: 0.0625,
			kg: 0.0283495,
			LT: 0.0000283495,
			ST: 0.00003125,
			mt: 0.0000283495,
			µg: 28349523.1
			// Add more conversions here
		},
		LT: {
			lb: 2204.62,
			oz: 35274,
			kg: 1000,
			ST: 1.10231,
			mt: 1,
			µg: 1000000000000
			// Add more conversions here
		},
		ST: {
			lb: 2000,
			oz: 32000,
			kg: 907.185,
			LT: 0.907185,
			mt: 0.907185,
			µg: 907184740000
			// Add more conversions here
		},
		mt: {
			lb: 2204.62,
			oz: 35274,
			kg: 1000,
			LT: 1,
			ST: 1.10231,
			µg: 1000000000000
			// Add more conversions here
		},
		µg: {
			lb: 2.20462e-9,
			oz: 3.5274e-8,
			kg: 1e-9,
			LT: 1e-12,
			ST: 1.10231e-12,
			mt: 1e-12
			// Add more conversions here
		}
		// Add more units here
	};
	let inputValue = 0;
	let selectedUnitValueIn = 'lb';
	let selectedUnitValueOut = 'kg'
	let convertedWeightText = '';


	function convertUnit(value, fromUnit, toUnit) {
		
  if (fromUnit === toUnit) {
    return value;
  }

  const conversionFactor = conversionTable[fromUnit][toUnit];

  if (conversionFactor === undefined) {
    throw new Error(`Cannot convert from ${fromUnit} to ${toUnit}`);
  }

  return value * conversionFactor;
}

	function convertWeight() {
		const weightInput = inputValue;
		
		
		let convertedWeight = convertUnit(weightInput ,selectedUnitValueIn , selectedUnitValueOut );

		convertedWeightText = `Converted weight: ${convertedWeight.toFixed(2)} ${selectedUnitValueOut}`;
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<h1>Weight Conversion Calculator</h1>
<form>
	<label for="weight">Enter weight:</label>
	<input bind:value={inputValue} type="number" id="weight" name="weight" required />
	<select id="unit" name="unit" bind:value={selectedUnitValueIn}>
		<option value="lb">Pounds (lb)</option>
		<option value="mt">Metric Ton (mt)</option>
		<option value="ST">Short Ton (ST)</option>
		<option value="LT">Long Tons (LT)</option>
		<option value="oz">Ounces (oz)</option>
		<option value="µg">Micrograms (µg)</option>
		<option value="kg">Kilograms (kg)</option>
	</select>
	<select id="unit" name="unit" bind:value={selectedUnitValueOut}>
		<option value="lb">Pounds (lb)</option>
		<option value="mt">Metric Ton (mt)</option>
		<option value="ST">Short Ton (ST)</option>
		<option value="LT">Long Tons (LT)</option>
		<option value="oz">Ounces (oz)</option>
		<option value="µg">Micrograms (µg)</option>
		<option value="kg">Kilograms (kg)</option>
	</select>
	<button on:click={convertWeight}>Convert</button>
</form>
<p id="result">
	{convertedWeightText}
</p>
