# arve
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arvé</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: Arial, sans-serif;
            background: #0d0d0d;
            color: white;
            min-height: 100vh;
        }

        header {
            padding: 20px;
            text-align: center;
            border-bottom: 1px solid #333;
        }

        header h1 {
            font-family: Georgia, serif;
            font-size: 34px;
            letter-spacing: 4px;
        }

        header p {
            color: #aaa;
            margin-top: 5px;
        }

        .app {
            max-width: 1000px;
            margin: auto;
            padding: 25px;
        }

        .menu {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 25px;
        }

        button {
            background: #151515;
            color: white;
            border: 1px solid #444;
            padding: 12px 18px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 15px;
        }

        button:hover {
            background: #222;
        }

        .designer {
            display: grid;
            grid-template-columns: 1fr 300px;
            gap: 25px;
        }

        .design-area {
            min-height: 550px;
            background: #161616;
            border: 1px solid #333;
            border-radius: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .shirt {
            width: 250px;
            height: 300px;
            background: white;
            position: relative;
            clip-path: polygon(
                25% 5%,
                40% 0%,
                50% 8%,
                60% 0%,
                75% 5%,
                100% 25%,
                85% 40%,
                72% 30%,
                72% 100%,
                28% 100%,
                28% 30%,
                15% 40%,
                0% 25%
            );
            transition: 0.3s;
        }

        .shirt-text {
            position: absolute;
            top: 45%;
            width: 100%;
            text-align: center;
            color: black;
            font-size: 25px;
            font-weight: bold;
        }

        .controls {
            background: #161616;
            border: 1px solid #333;
            border-radius: 15px;
            padding: 20px;
        }

        .controls h2 {
            font-family: Georgia, serif;
            margin-bottom: 20px;
        }

        .control {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #bbb;
        }

        input,
        select {
            width: 100%;
            padding: 10px;
            border-radius: 7px;
            border: 1px solid #444;
            background: #222;
            color: white;
        }

        .colors {
            display: flex;
            gap: 10px;
        }

        .color {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            border: 2px solid white;
            cursor: pointer;
        }

        .black {
            background: #111;
        }

        .white {
            background: white;
        }

        .green {
            background: #183b2b;
        }

        .red {
            background: #541c27;
        }

        @media (max-width: 750px) {
            .designer {
                grid-template-columns: 1fr;
            }

            .design-area {
                min-height: 450px;
            }
        }
    </style>
</head>

<body>

<header>
    <h1>ARVÉ</h1>
    <p>Design it your way.</p>
</header>

<div class="app">

    <div class="menu">
        <button onclick="changeClothing('T-Shirt')">T-Shirt</button>
        <button onclick="changeClothing('Hemd')">Hemd</button>
        <button onclick="changeClothing('Hose')">Hose</button>
    </div>

    <div class="designer">

        <div class="design-area">
            <div class="shirt" id="clothing">
                <div class="shirt-text" id="shirtText">
                    ARVÉ
                </div>
            </div>
        </div>

        <div class="controls">

            <h2>Designer</h2>

            <div class="control">
                <label>Farbe</label>

                <div class="colors">
                    <div class="color black" onclick="changeColor('#111111')"></div>
                    <div class="color white" onclick="changeColor('#ffffff')"></div>
                    <div class="color green" onclick="changeColor('#183b2b')"></div>
                    <div class="color red" onclick="changeColor('#541c27')"></div>
                </div>
            </div>

            <div class="control">
                <label>Text</label>
                <input
                    type="text"
                    placeholder="Dein Text..."
                    oninput="changeText(this.value)"
                >
            </div>

            <div class="control">
                <label>Textgröße</label>

                <input
                    type="range"
                    min="10"
                    max="60"
                    value="25"
                    oninput="changeTextSize(this.value)"
                >
            </div>

            <button onclick="saveDesign()">
                Design speichern
            </button>

        </div>

    </div>
</div>

<script>

    const clothing = document.getElementById("clothing");
    const shirtText = document.getElementById("shirtText");

    function changeColor(color) {
        clothing.style.background = color;

        if (color === "#ffffff") {
            shirtText.style.color = "black";
        } else {
            shirtText.style.color = "white";
        }
    }

    function changeText(text) {
        shirtText.textContent = text || "ARVÉ";
    }

    function changeTextSize(size) {
        shirtText.style.fontSize = size + "px";
    }

    function changeClothing(type) {

        if (type === "T-Shirt") {
            clothing.style.width = "250px";
            clothing.style.height = "300px";
            clothing.style.borderRadius = "0";
        }

        if (type === "Hemd") {
            clothing.style.width = "240px";
            clothing.style.height = "310px";
            clothing.style.borderRadius = "8px";
        }

        if (type === "Hose") {
            clothing.style.width = "180px";
            clothing.style.height = "350px";
            clothing.style.clipPath = "polygon(10% 0%, 90% 0%, 80% 100%, 55% 100%, 50% 55%, 45% 100%, 20% 100%)";
        }

        if (type === "T-Shirt") {
            clothing.style.clipPath =
                "polygon(25% 5%, 40% 0%, 50% 8%, 60% 0%, 75% 5%, 100% 25%, 85% 40%, 72% 30%, 72% 100%, 28% 100%, 28% 30%, 15% 40%, 0% 25%)";
        }
    }

    function saveDesign() {
        alert("Dein Arvé-Design wurde gespeichert!");
    }

</script>

</body>
</html>
2
<script>

const clothing = document.getElementById("clothing");
const shirtText = document.getElementById("shirtText");

let dragging = false;
let offsetX = 0;
let offsetY = 0;

// Farbe ändern
function changeColor(color) {
    clothing.style.background = color;

    if (color === "#ffffff") {
        shirtText.style.color = "black";
    } else {
        shirtText.style.color = "white";
    }
}

// Text ändern
function changeText(text) {
    shirtText.textContent = text || "ARVÉ";
}

// Textgröße ändern
function changeTextSize(size) {
    shirtText.style.fontSize = size + "px";
}

// Kleidung wechseln
function changeClothing(type) {

    if (type === "T-Shirt") {
        clothing.style.width = "250px";
        clothing.style.height = "300px";
        clothing.style.clipPath =
            "polygon(25% 5%,40% 0%,50% 8%,60% 0%,75% 5%,100% 25%,85% 40%,72% 30%,72% 100%,28% 100%,28% 30%,15% 40%,0% 25%)";
    }

    if (type === "Hemd") {
        clothing.style.width = "240px";
        clothing.style.height = "310px";
        clothing.style.clipPath = "none";
        clothing.style.borderRadius = "8px";
    }

    if (type === "Hose") {
        clothing.style.width = "180px";
        clothing.style.height = "350px";
        clothing.style.clipPath =
            "polygon(10% 0%,90% 0%,80% 100%,55% 100%,50% 55%,45% 100%,20% 100%)";
    }
}

// ----------------------------
// FINGER-STEUERUNG
// ----------------------------

shirtText.addEventListener("pointerdown", startDrag);

function startDrag(e) {

    dragging = true;

    const rect = shirtText.getBoundingClientRect();

    offsetX = e.clientX - rect.left;
    offsetY = e.clientY - rect.top;

    shirtText.setPointerCapture(e.pointerId);
}

shirtText.addEventListener("pointermove", drag);

function drag(e) {

    if (!dragging) return;

    const clothingRect = clothing.getBoundingClientRect();

    let x = e.clientX - clothingRect.left - offsetX;
    let y = e.clientY - clothingRect.top - offsetY;

    shirtText.style.left = x + "px";
    shirtText.style.top = y + "px";

    shirtText.style.transform = "none";
}

shirtText.addEventListener("pointerup", stopDrag);
shirtText.addEventListener("pointercancel", stopDrag);

function stopDrag() {
    dragging = false;
}

// Design speichern
function saveDesign() {

    const design = {
        color: clothing.style.background,
        text: shirtText.textContent,
        size: shirtText.style.fontSize,
        x: shirtText.style.left,
        y: shirtText.style.top
    };

    localStorage.setItem("arveDesign", JSON.stringify(design));

    alert("Arvé-Design gespeichert!");
}

</script>
	◦	3

<div class="menu">
    <button onclick="changeClothing('T-Shirt')">T-Shirt</button>
    <button onclick="changeClothing('Hemd')">Hemd</button>
    <button onclick="changeClothing('Hose')">Hose</button>

    <button onclick="addSticker('★')">⭐ Stern</button>
    <button onclick="addSticker('✦')">✦ Symbol</button>
    <button onclick="addSticker('ARVÉ')">ARVÉ</button>
</div>

4

Und direkt vor </script> in deinem JavaScript einfügen:

function addSticker(symbol) {

    const sticker = document.createElement("div");

    sticker.textContent = symbol;

    sticker.style.position = "absolute";
    sticker.style.left = "50%";
    sticker.style.top = "50%";
    sticker.style.transform = "translate(-50%, -50%)";
    sticker.style.fontSize = "45px";
    sticker.style.fontWeight = "bold";
    sticker.style.color = "white";
    sticker.style.cursor = "grab";
    sticker.style.touchAction = "none";
    sticker.style.userSelect = "none";
    sticker.style.zIndex = "10";

    clothing.appendChild(sticker);

    let moving = false;
    let offsetX = 0;
    let offsetY = 0;

    sticker.addEventListener("pointerdown", function(e) {

        moving = true;

        const rect = sticker.getBoundingClientRect();

        offsetX = e.clientX - rect.left;
        offsetY = e.clientY - rect.top;

        sticker.setPointerCapture(e.pointerId);
    });

    sticker.addEventListener("pointermove", function(e) {

        if (!moving) return;

        const clothingRect = clothing.getBoundingClientRect();

        const x = e.clientX - clothingRect.left - offsetX;
        const y = e.clientY - clothingRect.top - offsetY;

        sticker.style.left = x + "px";
        sticker.style.top = y + "px";
        sticker.style.transform = "none";
    });

    sticker.addEventListener("pointerup", function() {
        moving = false;
    });

    sticker.addEventListener("pointercancel", function() {
        moving = false;
    });
}