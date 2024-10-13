<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Store</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: white;
            color: #0044cc;
        }
        .container {
            width: 80%;
            margin: auto;
            padding: 20px;
        }
        .product {
            border: 2px solid #0044cc;
            padding: 10px;
            margin-bottom: 20px;
            text-align: center;
        }
        .hidden {
            display: none;
        }
        button {
            background-color: #0044cc;
            color: white;
            border: none;
            padding: 10px;
            cursor: pointer;
        }
        button:hover {
            background-color: #003399;
        }
        .result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Product Store</h1>

        <div class="product">
            <h2>Rank 30</h2>
            <img src="rank30.png" alt="Rank 30" width="100">
            <button onclick="openRank30Modal()">Select</button>
        </div>

        <div class="product">
            <h2>Rank 35</h2>
            <img src="rank35.png" alt="Rank 35" width="100">
            <button onclick="openRank35Modal()">Select</button>
        </div>

        <div class="product">
            <h2>Ranked</h2>
            <img src="ranked.png" alt="Ranked" width="100">
            <button onclick="openRankedModal()">Select</button>
        </div>

        <!-- Rank 30 Modal -->
        <div id="rank30Modal" class="hidden">
            <h3>Enter current trophies (from 500 to 999):</h3>
            <input type="number" id="rank30Cups" min="500" max="999">
            <button onclick="calculateRank30Price()">Get Price</button>
            <div id="rank30Result" class="result"></div>
        </div>

        <!-- Rank 35 Modal -->
        <div id="rank35Modal" class="hidden">
            <h3>Select your fighter's power level:</h3>
            <select id="rank35PowerLevel">
                <option value="9">9</option>
                <option value="10">10</option>
                <option value="11">11</option>
                <option value="Hypercharged">Hypercharged</option>
            </select>
            <h3>Enter current trophies (from 500 to 1249):</h3>
            <input type="number" id="rank35Cups" min="500" max="1249">
            <button onclick="calculateRank35Price()">Get Price</button>
            <div id="rank35Result" class="result"></div>
        </div>

        <!-- Ranked Modal -->
        <div id="rankedModal" class="hidden">
            <h3>Select current rank:</h3>
            <select id="rankedCurrentRank">
                <option value="Bronze">Bronze</option>
                <option value="Silver">Silver</option>
                <option value="Gold">Gold</option>
                <option value="Diamond">Diamond</option>
                <option value="Mythic">Mythic</option>
                <option value="Legendary">Legendary</option>
                <option value="Master">Master</option>
            </select>
            <h3>Enter the number of fighters with level 9 or higher:</h3>
            <select id="rankedPowerLevelCount">
                <option value="Less than 5">Less than 5</option>
                <option value="5-9">5-9</option>
                <option value="10-19">10-19</option>
                <option value="20-29">20-29</option>
                <option value="More than 30">More than 30</option>
            </select>
            <h3>Select desired rank:</h3>
            <select id="rankedDesiredRank">
                <option value="Diamond">Diamond</option>
                <option value="Mythic">Mythic</option>
                <option value="Legendary">Legendary</option>
                <option value="Master">Master</option>
            </select>
            <button onclick="calculateRankedPrice()">Get Price</button>
            <div id="rankedResult" class="result"></div>
        </div>

        <div>
            <p>Contact us: <a href="https://wa.me/79265881185">WhatsApp</a> or <a href="https://discord.gg/GWaRP5FFRt">Discord</a></p>
        </div>
    </div>

    <script>
        function openRank30Modal() {
            document.getElementById('rank30Modal').classList.remove('hidden');
        }

        function openRank35Modal() {
            document.getElementById('rank35Modal').classList.remove('hidden');
        }

        function openRankedModal() {
            document.getElementById('rankedModal').classList.remove('hidden');
        }

        function calculateRank30Price() {
            const cups = parseInt(document.getElementById('rank30Cups').value);
            let price;

            if (cups >= 500 && cups <= 599) price = 11;
            else if (cups >= 600 && cups <= 749) price = 10;
            else if (cups >= 750 && cups <= 799) price = 9;
            else if (cups >= 800 && cups <= 849) price = 8;
            else if (cups >= 850 && cups <= 899) price = 7;
            else if (cups >= 900 && cups <= 949) price = 6;
            else if (cups >= 950 && cups <= 999) price = 5;
            else price = "Invalid value";

            document.getElementById('rank30Result').innerText = `Price: ${price}€`;
        }

        function calculateRank35Price() {
            const cups = parseInt(document.getElementById('rank35Cups').value);
            const powerLevel = document.getElementById('rank35PowerLevel').value;
            let price;

            if (powerLevel === '9') {
                if (cups >= 500 && cups <= 749) price = 44;
                else if (cups >= 750 && cups <= 999) price = 43;
                else if (cups >= 1000 && cups <= 1049) price = 42;
                else if (cups >= 1050 && cups <= 1099) price = 40;
                else if (cups >= 1100 && cups <= 1149) price = 37;
                else if (cups >= 1150 && cups <= 1199) price = 32;
                else if (cups >= 1200 && cups <= 1249) price = 28;
            } else if (powerLevel === '10') {
                if (cups >= 500 && cups <= 999) price = 42;
                else if (cups >= 1000 && cups <= 1049) price = 40;
                else if (cups >= 1050 && cups <= 1099) price = 38;
                else if (cups >= 1100 && cups <= 1149) price = 35;
                else if (cups >= 1150 && cups <= 1199) price = 30;
                else if (cups >= 1200 && cups <= 1249) price = 25;
            } else if (powerLevel === '11') {
                if (cups >= 500 && cups <= 999) price = 32;
                else if (cups >= 1000 && cups <= 1049) price = 31;
                else if (cups >= 1050 && cups <= 1099) price = 28;
                else if (cups >= 1100 && cups <= 1149) price = 25;
                else if (cups >= 1150 && cups <= 1199) price = 22;
                else if (cups >= 1200 && cups <= 1249) price = 19;
            } else if (powerLevel === 'Hypercharged') {
                if (cups >= 500 && cups <= 999) price = 30;
                else if (cups >= 1000 && cups <= 1049) price = 29;
                else if (cups >= 1050 && cups <= 1099) price = 27;
                else if (cups >= 1100 && cups <= 1149) price = 24;
                else if (cups >= 1150 && cups <= 1199) price = 22;
                else if (cups >= 1200 && cups <= 1249) price = 19;
            } else {
                price = "Invalid value";
            }

            document.getElementById('rank35Result').innerText = `Price: ${price}€`;
        }

        function calculateRankedPrice() {
            const currentRank = document.getElementById('rankedCurrentRank').value;
            const powerCount = document.getElementById('rankedPowerLevelCount').value;
            const desiredRank = document.getElementById('rankedDesiredRank').value;
            let price;

            // Price calculation logic based on current rank and power count
            const prices = {
                Bronze: {
                    'Less than 5': { Diamond: 8, Mythic: 14, Legendary: 25, Master: 40 },
                    '5-9': { Diamond: 7, Mythic: 13, Legendary: 23, Master: 38 },
                    '10-19': { Diamond: 6, Mythic: 12, Legendary: 21, Master: 35 },
                    '20-29': { Diamond: 6, Mythic: 12, Legendary: 20, Master: 34 }
                },
                Silver: {
                    'Less than 5': { Diamond: 7.5, Mythic: 13, Legendary: 22, Master: 39 },
                    '5-9': { Diamond: 7.2, Mythic: 12.5, Legendary: 21.2, Master: 38 },
                    '10-19': { Diamond: 7, Mythic: 12, Legendary: 20.5, Master: 37 },
                    '20-29': { Diamond: 6.5, Mythic: 11.4, Legendary: 19.5, Master: 35 }
                },
                Gold: {
                    'Less than 5': { Diamond: 5, Mythic: 10, Legendary: 21, Master: 37.5 },
                    '5-9': { Diamond: 5, Mythic: 10, Legendary: 18, Master: 35 },
                    '10-19': { Diamond: 5, Mythic: 7.5, Legendary: 15, Master: 28 },
                    '20-29': { Diamond: 5, Mythic: 7, Legendary: 12, Master: 25 }
                },
                Diamond: {
                    'Less than 5': { Mythic: 7.5, Legendary: 16, Master: 33 },
                    '5-9': { Mythic: 7, Legendary: 14, Master: 30 },
                    '10-19': { Mythic: 6, Legendary: 12, Master: 27.5 },
                    '20-29': { Mythic: 5, Legendary: 10, Master: 25 }
                },
                Mythic: {
                    'Less than 5': { Legendary: 11, Master: 30 },
                    '5-9': { Legendary: 10, Master: 28 },
                    '10-19': { Legendary: 9, Master: 25 },
                    '20-29': { Legendary: 8, Master: 23 }
                },
                Legendary: {
                    'Less than 5': { Master: 29 },
                    '5-9': { Master: 27 },
                    '10-19': { Master: 22 },
                    '20-29': { Master: 19.5 }
                }
            };

            // Fetch the price based on selected values
            if (prices[currentRank] && prices[currentRank][powerCount]) {
                price = prices[currentRank][powerCount][desiredRank] || "Invalid value";
            } else {
                price = "Invalid value";
            }

            document.getElementById('rankedResult').innerText = `Price: ${price}€`;
        }
    </script>
</body>
</html>
