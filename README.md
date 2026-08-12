<!DOCTYPE html>
<html>
<head>
    <title>SmartMall</title>

    <style>
        body {
            font-family: Arial;
            margin: 0;
            background: #f4f6f8;
        }

        header {
            background: #172b4d;
            color: white;
            padding: 25px;
            text-align: center;
        }

        .container {
            max-width: 700px;
            margin: 40px auto;
            padding: 20px;
        }

        input {
            width: 70%;
            padding: 14px;
            font-size: 16px;
        }

        button {
            padding: 14px 20px;
            background: #1677ff;
            color: white;
            border: none;
            cursor: pointer;
        }

        #result {
            margin-top: 30px;
            background: white;
            padding: 25px;
            border-radius: 10px;
            display: none;
        }

        .map {
            margin-top: 20px;
            padding: 30px;
            background: #e9eef5;
            text-align: center;
        }
    </style>
</head>

<body>

<header>
    <h1>🛍️ SmartMall</h1>
    <p>Find any product inside the mall</p>
</header>

<div class="container">

    <input id="search" placeholder="Search product...">

    <button onclick="findProduct()">Search</button>

    <div id="result"></div>

</div>

<script>

const products = [
    {
        name: "KitKat",
        price: 40,
        store: "Reliance Smart",
        floor: "2nd Floor",
        section: "Chocolate Section"
    },
    {
        name: "Dairy Milk",
        price: 50,
        store: "Spencer's",
        floor: "1st Floor",
        section: "Chocolate Section"
    },
    {
        name: "Laptop Charger",
        price: 1500,
        store: "Croma",
        floor: "3rd Floor",
        section: "Computer Accessories"
    }
];

function findProduct() {

    let search = document
        .getElementById("search")
        .value
        .toLowerCase();

    let product = products.find(p =>
        p.name.toLowerCase().includes(search)
    );

    let result = document.getElementById("result");

    result.style.display = "block";

    if (!product) {
        result.innerHTML = "<h3>❌ Product not found</h3>";
        return;
    }

    result.innerHTML = `
        <h2>🍫 ${product.name}</h2>

        <p><b>Price:</b> ₹${product.price}</p>

        <p>🏪 <b>Store:</b> ${product.store}</p>

        <p>📍 <b>Floor:</b> ${product.floor}</p>

        <p>🗂️ <b>Section:</b> ${product.section}</p>

        <p>✅ <b>Available</b></p>

        <button onclick="navigate()">
            Navigate
        </button>

        <div class="map" id="map"></div>
    `;
}

function navigate() {

    document.getElementById("map").innerHTML = `
        <h3>🗺️ Navigation</h3>

        <p>Entrance</p>
        ↓
        <p>Lift</p>
        ↓
        <p>2nd Floor</p>
        ↓
        <p>Reliance Smart</p>
        ↓
        <p>Chocolate Section</p>

        <h3>📍 You have arrived!</h3>
    `;
}

</script>

</body>
</html>
