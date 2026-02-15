<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Ascension: Cube-Bearer Trial</title>
<style>
    body {
        background: #0a0f1f;
        color: #cce6ff;
        font-family: Arial, sans-serif;
        padding: 20px;
    }
    #game-box {
        background: #11182e;
        padding: 20px;
        border-radius: 10px;
        width: 600px;
        margin: auto;
        box-shadow: 0 0 20px #4da6ff;
    }
    button {
        background: #1a75ff;
        color: white;
        border: none;
        padding: 12px 20px;
        margin: 10px;
        border-radius: 8px;
        cursor: pointer;
        font-size: 16px;
    }
    button:hover {
        background: #5599ff;
    }
</style>
</head>
<body>

<div id="game-box">
    <h1>ASCENSION: Cube-Bearer Trial</h1>
    <p id="story">Type START to begin your journey.</p>
    <div id="choices"></div>
</div>

<script>
let stage = "intro";

function updateStory(text, options = []) {
    document.getElementById("story").innerText = text;

    let choiceBox = document.getElementById("choices");
    choiceBox.innerHTML = "";

    options.forEach(opt => {
        let btn = document.createElement("button");
        btn.innerText = opt.label;
        btn.onclick = () => opt.action();
        choiceBox.appendChild(btn);
    });
}

function startGame() {
    stage = "trial1";
    updateStory(
        "The cube glows. A single arrow flashes: RIGHT.",
        [
            { label: "MOVE RIGHT", action: trial1 },
            { label: "MOVE LEFT", action: trial1 },
            { label: "HOVER UP", action: trial1 },
            { label: "STAY STILL", action: trial1 }
        ]
    );
}

function trial1() {
    stage = "trial2";
    updateStory(
        "Trial Two begins. Arrows flash rapidly around you.",
        [
            { label: "MOVE LEFT", action: trial2 },
            { label: "DOUBLE FORWARD", action: trial2 },
            { label: "HOVER UP", action: trial2 },
            { label: "DROP DOWN", action: trial2 }
        ]
    );
}

function trial2() {
    stage = "trial3";
    updateStory(
        "Trial Three: Momentum. A long moving course appears.",
        [
            { label: "WALK", action: trial3 },
            { label: "HOVER FORWARD", action: trial3 },
            { label: "DOUBLE FORWARD", action: trial3 },
            { label: "MIX MOVES", action: trial3 }
        ]
    );
}

function trial3() {
    stage = "final";
    updateStory(
        "Final Trial: Ascension. A vertical spiral rises into the sky.",
        [
            { label: "LEAP", action: finalTrial },
            { label: "HOVER UP", action: finalTrial },
            { label: "DOUBLE FORWARD", action: finalTrial },
            { label: "SECRET PATH", action: finalTrial }
        ]
    );
}

function finalTrial() {
    stage = "ending";
    updateStory(
        "You reach the Ascension Core. The chamber waits for your final move.",
        [
            { label: "WALK TO THE CORE", action: ending },
            { label: "HOVER TO THE CORE", action: ending },
            { label: "DOUBLE FORWARD", action: ending },
            { label: "LET THE CUBE CONNECT", action: ending }
        ]
    );
}

function ending() {
    updateStory(
        "Ascension complete. You are now Cube‑Bearer Prime. The tower bows to your presence.",
        []
    );
}

document.addEventListener("keydown", function(e) {
    if (e.key.toLowerCase() === "start") startGame();
});

updateStory("Type START to begin your journey.", [
    { label: "START", action: startGame }
]);
</script>

</body>
</html>


