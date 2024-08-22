
    
<svelte:head>
  <meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta name="description"
			content="Convert fuel efficiency metrics like MPG to Liters per 100km, MPG (UK) to L/100km, and MPG to Km/L with detailed explanations and theoretical background.">
		<meta name="keywords"
			content="MPG to Liters, Fuel Efficiency Conversion, Kilometers per Liter, MPG to Km/L, MPG UK to L/100km">
		<meta name="robots" content="index, follow">
		<title>Fuel Efficiency Conversion Calculators</title>
</svelte:head> 

<div>
    <header>
        <img src="/static/logo.png" alt="Fuel Efficiency Conversion Logo" class="logo">
        <h1>Fuel Efficiency Conversion Calculators</h1>
        <p>Convert MPG to Liters, Km/L, and more with in-depth explanations</p>
    </header>

    <!-- <nav>
        <a href="#">Home</a>
        <a href="#">MPG to Liters per 100km</a>
        <a href="#">MPG (UK) to L/100km</a>
        <a href="#">MPG to Km/L</a>
        <a href="#">Other Calculators</a>
    </nav> -->

    <div class="container">
        <!-- MPG to Liters per 100 Kilometers -->
        <div class="card">
            <h2>MPG (US) to Liters per 100 Kilometers (L/100km)</h2>
            <p>Convert Miles Per Gallon (MPG) to Liters per 100 kilometers (L/100km). This conversion is commonly used to measure fuel efficiency in many countries, particularly in Europe and Canada.</p>
            <div class="input-group">
                <label for="mpg">Miles Per Gallon (MPG US):</label>
                <input type="number" id="mpg" placeholder="Enter MPG">
            </div>
            <button class="button" onclick="convertToL100km()">Convert</button>
            <p class="result" id="resultL100km"></p>
            <div class="explanation">
                <h3>Understanding the Conversion</h3>
                <p>Fuel efficiency is often measured in Miles Per Gallon (MPG) in the United States, indicating how many miles a vehicle can travel on one gallon of fuel. However, many countries prefer the Liters per 100 kilometers (L/100km) metric, which shows the amount of fuel consumed for every 100 kilometers traveled. This conversion is crucial for understanding and comparing vehicle efficiency across different regions.</p>
                <p>The formula to convert MPG to L/100km is:<br>
                <code>L/100km = 235.214583 / MPG</code></p>
                <p>This equation reflects the inverse relationship between fuel efficiency and fuel consumption: as MPG increases, indicating better fuel efficiency, the L/100km value decreases, meaning less fuel is used per 100 kilometers.</p>
            </div>
        </div>

        <!-- MPG (UK) to Liters per 100 Kilometers -->
        <div class="card">
            <h2>MPG (UK) to Liters per 100 Kilometers (L/100km)</h2>
            <p>Convert Miles Per Gallon (UK) to Liters per 100 kilometers (L/100km). This conversion accounts for the difference in gallon sizes between the UK and the US.</p>
            <div class="input-group">
                <label for="mpgUk">Miles Per Gallon (MPG UK):</label>
                <input type="number" id="mpgUk" placeholder="Enter MPG (UK)">
            </div>
            <button class="button" onclick="convertUkToL100km()">Convert</button>
            <p class="result" id="resultUkL100km"></p>
            <div class="explanation">
                <h3>Understanding the Conversion</h3>
                <p>The UK gallon is larger than the US gallon, which affects the MPG value when converting to L/100km. Therefore, it's essential to use the correct formula when performing these conversions.</p>
                <p>The formula to convert MPG (UK) to L/100km is:<br>
                <code>L/100km = 282.4809363 / MPG (UK)</code></p>
                <p>This equation adjusts for the difference in gallon sizes, ensuring accurate conversion for UK measurements.</p>
            </div>
        </div>

        <!-- MPG to Kilometers per Liter -->
        <div class="card">
            <h2>MPG to Kilometers per Liter (Km/L)</h2>
            <p>Convert Miles Per Gallon (MPG) to Kilometers per Liter (Km/L), a common metric used in many countries to measure fuel efficiency.</p>
            <div class="input-group">
                <label for="mpgToKmL">Miles Per Gallon (MPG):</label>
                <input type="number" id="mpgToKmL" placeholder="Enter MPG">
            </div>
            <button class="button" onclick="convertToKmL()">Convert</button>
            <p class="result" id="resultKmL"></p>
            <div class="explanation">
                <h3>Understanding the Conversion</h3>
                <p>Kilometers per Liter (Km/L) is a metric used in many countries, especially in Asia and Latin America. It indicates how many kilometers a vehicle can travel on one liter of fuel. The conversion from MPG to Km/L helps in understanding and comparing vehicle efficiency across different regions and standards.</p>
                <p>The formula to convert MPG to Km/L is:<br>
                <code>Km/L = MPG × 0.425144</code></p>
                <p>This formula accounts for the conversion from miles to kilometers and from gallons to liters, providing an accurate Km/L value.</p>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2024 Fuel Efficiency Conversions. All Rights Reserved.</p>
    </footer>

    
</div>


<script>
        function convertToL100km() {
            const mpg = document.getElementById('mpg').value;
            if(mpg && mpg > 0) {
                const result = 235.214583 / mpg;
                document.getElementById('resultL100km').innerText = `Result: ${result.toFixed(2)} L/100km`;
            } else {
                alert('Please enter a valid MPG value.');
            }
        }

        function convertUkToL100km() {
            const mpgUk = document.getElementById('mpgUk').value;
            if(mpgUk && mpgUk > 0) {
                const result = 282.4809363 / mpgUk;
                document.getElementById('resultUkL100km').innerText = `Result: ${result.toFixed(2)} L/100km`;
            } else {
                alert('Please enter a valid MPG (UK) value.');
            }
        }
        

        function convertToKmL() {
            const mpgToKmL = document.getElementById('mpgToKmL').value;
            if(mpgToKmL && mpgToKmL > 0) {
                const result = mpgToKmL * 0.425144;
                document.getElementById('resultKmL').innerText = `Result: ${result.toFixed(2)} Km/L`;
            } else {
                alert('Please enter a valid MPG value.');
            }
        }
    </script>

