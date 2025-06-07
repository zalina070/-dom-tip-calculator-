# -dom-tip-calculator-
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Tip Calculator</title>
    <style>
        body {
            background-color: rgb(10, 10, 88);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            text-align: center;
            color: aqua;
            margin: 0;
            padding: 0;
        }
        
        .container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        
        .wrapper {
            background: none;
            padding: 20px;
            border-radius: 10px;
        }
        
        input,
        select {
            width: 300px;
            padding: 10px;
            font-size: 16px;
            margin: 10px 0;
            border-radius: 6px;
            border: none;
            text-align: center;
        }
        
        #calculate {
            background-color: lightblue;
            color: black;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            margin-top: 20px;
            cursor: pointer;
            border-radius: 6px;
            transition: background-color 0.3s ease;
        }
        
        #calculate:hover {
            background-color: deepskyblue;
        }
        
        #tip,
        #result,
        #each {
            visibility: hidden;
            font-size: 18px;
            font-weight: bold;
            margin-top: 10px;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="wrapper">
            <h1>Tip calculator</h1>
            <p>How much was your bill?</p>
            <input type="number" id="bill">

            <p>How was your service?</p>
            <select id="service">
        <option value="30">30% – Outstanding</option>
        <option value="20">20% – Good</option>
        <option value="15">15% – It was OK</option>
        <option value="10">10% – Bad</option>
        <option value="5">5% – Terrible</option>
      </select>

            <p>How many people are sharing the bill?</p>
            <input type="number" id="people">

            <div>
                <p id="tip">Tip amount:</p>
                <span id="result"></span>
                <span id="each"></span>
            </div>

            <button id="calculate">Calculate</button>
        </div>
    </div>

    <script>
        const bill = document.querySelector("#bill");
        const service = document.querySelector("#service");
        const people = document.querySelector("#people");
        const result = document.querySelector("#result");
        const each = document.querySelector("#each");
        const button = document.querySelector("#calculate");
        const tip = document.querySelector("#tip");

        button.addEventListener("click", calculate);

        function calculate() {
            let index = service.selectedIndex;
            let totalTip = Number(bill.value) * Number(service.options[index].value) / 100;

            tip.style.visibility = "visible";
            result.style.visibility = "visible";

            if (people.value > 1) {
                result.innerHTML = (totalTip / Number(people.value)).toFixed(2) + " per person";
                each.style.visibility = "visible";
            } else {
                result.innerHTML = totalTip.toFixed(2);
                each.style.visibility = "hidden";
            }
        }
    </script>
</body>

</html>
