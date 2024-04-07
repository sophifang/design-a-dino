<script>
    let page = 0;
    let diet;
    let region;
    let type;
    let length;
    let name;
    let imgNum = 0;
    function next() {
        page++;
        console.log(name);
    }
    function nextImg() {
        imgNum++;
    }
    function prevImg() {
        if (imgNum === 0) {
            imgNum = 5;
        } else {
            imgNum--;
        }
    }
    function selectDiet(selectedDiet) {
        diet = selectedDiet;
    }
    function selectRegion(selectedRegion) {
        region = selectedRegion;
    }
    function selectType(selectedType) {
        type = selectedType;
    }
    function selectLength(selectedLength) {
        length = selectedLength;
    }
    function selectDinoName() {
        name = document.getElementById("dino-name").value;
        console.log(name);
    }
</script>

<main>
    <!-- home -->
    {#if page === 0}
        <div class = "home">
            <img class = "background" src = "dino-home.png"/>
            <button on:click={next}>LET'S GO!</button>
        </div>
    {/if}
    <!-- Dino Diet -->
    {#if page === 1}
        <div class = "page">
            <img class = "background" src="dino-question.png"/>
            <div class = "question-box">
            <h2>Dino Diet</h2>
            <div class = "row">
                <div class = "column" on:click={() => selectDiet("herbivore")} style={`border: solid 2px ${diet === "herbivore" ? "#D9D9D9" : "#fff"}; background-color: ${diet === "herbivore" ? "#f5f5f5" : "#fff"}`}>
                <h3>Herbivore</h3>
                <img class = "icon" src = "herbivore.png"/>
                </div>
                <div class = "column" on:click={() => selectDiet("carnivore")} style={`border: solid 2px ${diet === "carnivore" ? "#D9D9D9" : "#fff"}; background-color: ${diet === "carnivore" ? "#f5f5f5" : "#fff"}`}>
                <h3>Carnivore</h3>
                <img class = "icon" src = "carnivore.png"/>
                </div>
                <div class = "column" on:click={() => selectDiet("omnivore")} style={`border: solid 2px ${diet === "omnivore" ? "#D9D9D9" : "#fff"}; background-color: ${diet === "omnivore" ? "#f5f5f5" : "#fff"}`}>
                <h3>Omnivore</h3>
                <img class = "icon" src = "omnivore.png"/>
                </div>
            </div>
            <button on:click={next}>NEXT</button>
            </div>
        </div>
    {/if}

    <!-- Dino Region -->
    {#if page === 2}
        <div class = "region">
            <img class = "background" src="dino-question.png"/>
            <div class = "question-box">
            <h2>Dino Region</h2>
            <div class = "row">
                <div class = "column" on:click={() => selectRegion("asia")} style={`border: solid 2px ${region === "asia" ? "#D9D9D9" : "#fff"}; background-color: ${region === "asia" ? "#f5f5f5" : "#fff"}`}>
                <h3>Asia</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("africa")} style={`border: solid 2px ${region === "africa" ? "#D9D9D9" : "#fff"}; background-color: ${region === "africa" ? "#f5f5f5" : "#fff"}`}>
                <h3>Africa</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("north america")} style={`border: solid 2px ${region === "north america" ? "#D9D9D9" : "#fff"}; background-color: ${region === "north america" ? "#f5f5f5" : "#fff"}`}>
                <h3>North America</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("south america")} style={`border: solid 2px ${region === "south america" ? "#D9D9D9" : "#fff"}; background-color: ${region === "south america" ? "#f5f5f5" : "#fff"}`}>
                <h3>South America</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("antartica")} style={`border: solid 2px ${region === "antartica" ? "#D9D9D9" : "#fff"}; background-color: ${region === "antartica" ? "#f5f5f5" : "#fff"}`}>
                <h3>Antartica</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("europe")} style={`border: solid 2px ${region === "europe" ? "#D9D9D9" : "#fff"}; background-color: ${region === "europe" ? "#f5f5f5" : "#fff"}`}>
                <h3>Europe</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("oceania")} style={`border: solid 2px ${region === "oceania" ? "#D9D9D9" : "#fff"}; background-color: ${region === "oceania" ? "#f5f5f5" : "#fff"}`}>
                <h3>Oceania</h3>
                </div>
            </div>
            <button on:click={next}>NEXT</button>
            </div>
        </div>
    {/if}

    <!-- Dino Type -->
    {#if page === 3}
        <div class = "type">
            <img class = "background" src="dino-question.png"/>
            <div class = "question-box">
            <h2>Dino Type</h2>
            <div class = "row">
                <div>
                    <img on:click={prevImg}  class = "icon" src = "left-arrow.png"/>
                </div>
                {#if imgNum % 6 === 0}
                    <div class = "column" on:click={() => selectType("sauropod")} style={`border: solid 2px ${type === "sauropod" ? "#D9D9D9" : "#fff"}; background-color: ${type === "sauropod" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "sauropod.png"/>
                        <h3>Sauropod</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 1}
                    <div class = "column" on:click={() => selectType("ceratopsian")} style={`border: solid 2px ${type === "ceratopsian" ? "#D9D9D9" : "#fff"}; background-color: ${type === "ceratopsian" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "ceratopsian.png"/>
                        <h3>Ceratopsian</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 2}
                    <div class = "column" on:click={() => selectType("euornithopod")} style={`border: solid 2px ${type === "euornithopod" ? "#D9D9D9" : "#fff"}; background-color: ${type === "euornithopod" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "euornithopod.png"/>
                        <h3>Euornithopod</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 3}
                    <div class = "column" on:click={() => selectType("small-theropod")} style={`border: solid 2px ${type === "small-theropod" ? "#D9D9D9" : "#fff"}; background-color: ${type === "small-theropod" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "small-theropod.png"/>
                        <h3>Small Theropod</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 4}
                    <div class = "column" on:click={() => selectType("large-theropod")} style={`border: solid 2px ${type === "large-theropod" ? "#D9D9D9" : "#fff"}; background-color: ${type === "large-theropod" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "large-theropod.png"/>
                        <h3>Large Theropod</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 5}
                    <div class = "column" on:click={() => selectType("armoured-dinosaur")} style={`border: solid 2px ${type === "armoured-dinosaur" ? "#D9D9D9" : "#fff"}; background-color: ${type === "armoured-dinosaur" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "armoured-dinosaur.png"/>
                        <h3>Armoured Dinosaur</h3>
                    </div>
                {/if}
                <div>
                    <img on:click={nextImg} class = "icon" src = "right-arrow.png"/>
                </div>
            </div>
            <h4>Click the arrow buttons to explore more dinosaur types.</h4>
            <button on:click={next}>NEXT</button>
            </div>
        </div>
    {/if}

    <!-- Dino Length -->
    {#if page === 4}
        <div class = "page">
            <img class = "background" src="dino-question.png"/>
            <div class = "question-box">
            <h2>Dino Length</h2>
            <div class = "row">
                <div class = "column" on:click={() => selectLength("short")} style={`border: solid 2px ${length === "short" ? "#D9D9D9" : "#fff"}; background-color: ${length === "short" ? "#f5f5f5" : "#fff"}`}>
                    <h3>Short</h3>
                    <img class = "icon" src = "short.png"/>
                </div>
                <div class = "column" on:click={() => selectLength("medium")} style={`border: solid 2px ${length === "medium" ? "#D9D9D9" : "#fff"}; background-color: ${length === "medium" ? "#f5f5f5" : "#fff"}`}>
                    <h3>Medium</h3>
                    <img class = "icon" src = "medium.png"/>
                </div>
                <div class = "column" on:click={() => selectLength("long")} style={`border: solid 2px ${length === "long" ? "#D9D9D9" : "#fff"}; background-color: ${length === "long" ? "#f5f5f5" : "#fff"}`}>
                    <h3>Long</h3>
                    <img class = "icon" src = "long.png"/>
                </div>
            </div>
            <button on:click={next}>NEXT</button>
            </div>
        </div>
    {/if}

    <!-- Dino Name -->
    {#if page === 5}
        <div class = "page">
        <img class = "background" src="dino-question.png"/>
        <div class = "question-box">
            <h2>Dino Name</h2>
            <div class = "name-card">
                <img class = "icon" src = "name.png"/>
                <input type="text" placeholder="Name Your Dino!" id = "dino-name">
            </div>
            <button on:click={() => {selectDinoName(); next();}}>GENERATE DINO!</button>
        </div>
        </div>
    {/if}
    <!-- Egg Hatching Scene -->
    {#if page === 6}
        <div class = "home">
            <img class = "background" src = "whole-egg.png"/>
            <button on:click={next}>CLICK ME!</button>
        </div>
    {/if}
    {#if page === 7}
        <div class = "home">
            <img class = "background" src = "egg-cracking.png"/>
            <button on:click={next}>CLICK ME!</button>
        </div>
    {/if}
    {#if page === 8}
    <div class = "home">
        <img class = "background" src = "egg-more-cracking.png"/>
        <button on:click={next}>CLICK ME!</button>
    </div>
    {/if}
    {#if page === 9}
    <div class = "home">
        <img class = "background" src = "egg-full-cracked.png"/>
        <button on:click={next}>CLICK ME!</button>
    </div>
    {/if}
    {#if page === 10}
    <div class = "home">
        <img class = "background" src = "reveal-dino.png"/>
        <button on:click={next}>REVEAL DINOSAUR!</button>
    </div>
    {/if}
    <!-- Dino Reveal -->
    {#if page === 11}
    <div class = "dino-fact">
        <img class = "background" src="dino-question.png"/>
        <img class = "frame" src="frame.png"/>
        <div class = "question-box">
            <h2>Dino Reveal</h2>
            <p>{name} is a(n) Aardonyx, which is a Sauropod. It lived during the Jurassic period in Africa and was a {diet}. It was approximately 8.0m long.</p>
            <button>EXPLORE MORE DINOS!</button>
        </div>
    </div>
    {/if}
</main>

<style>
    main {
        font-family: 'Quicksand';
    }
    .background {
        width: 100%;
        height: auto;
        background-attachment: fixed;
        z-index: -1;
        position: absolute;
    }
    .frame {
        width: 93%;
        height: auto;
        background-attachment: fixed;
        margin-top: 120px;
        position: absolute;
        z-index: -1;
    }
    .dino-fact .question-box {
        background-color: transparent;
    }
    .home {
        display: flex;
        justify-content: center;
        
    }
    .page {
        display: flex;
        justify-content: center;
    }
    .dino-fact {
        display: flex;
        justify-content: center;
    }
    .region {
        display: flex;
        justify-content: center;
    }
    .type {
        display: flex;
        justify-content: center;
    }
    .type .column {
        border-radius: 0;
        padding-top: 40px;
        padding-bottom: 20px;
        padding-left: 20px;
        padding-right: 20px;
        border-radius: 90px;
    }
    .type .column:hover {
        border-radius: 90px;
    }
    .region .question-box {
        margin-top: 30%;
    }
    .question-box {
        margin: auto;
        background-color: white;
        width: 80%;
        height: 50%;
        border-radius: 50px;
        text-align: center;
        padding-top: 20px;
        padding-bottom: 20px;
        padding-left: 30px;
        padding-right: 30px;
        margin-top: 20%;
    }
    .region .row {
        flex-wrap: wrap;
    }
    .region .column {
        flex: 20%;
        padding-top:.5%;
        padding-bottom: .5%;
        padding-left:1%;
        padding-right:1%;
    }
    .row {
        display: flex;
        width:100%;
        justify-content: center;
        align-items: center;
    }
    .column {
        flex: 33.33%;
        padding: 20px;
        border-radius: 15%;
        margin: 10px;
    }
    .column:hover {
        background-color: #F5F5F5;
        border-radius: 15%;
        outline: 2px solid #D9D9D9;
        outline-offset: -2px;
    }
    .icon {
        width: 80%;
    }
    h2 {
        font-size: 30px;
        font-family: 'Delius Unicase';
    }
    h3 {
        font-size: 20px;
        font-family: "Quicksand";
        font-weight: 700;
    }
    button {
        font-family: 'Delius Unicase';
        font-weight: bold;
        font-size: 20px;
        background-color: #003FC5;
        border-radius: 50px;
        color:white;
        border:0px;
        padding-top:1%;
        padding-bottom: 1%;
        padding-left:3%;
        padding-right:3%;
    }
    .region .column {
        border-radius: 50px;
    }
    .home button {
        margin-top: 55%;
    }
    button:hover {
        background-color: #002A84;
    }
    input[type=text] {
        width:70%;
        height: 70px;
        border-radius: 35px;
        bottom: 100rem;
        font-size: 30px;
        font-family: 'Delius Unicase';
        padding: 10px;
        text-align: center;
    }
    .name-card {
        background-color: #009C90;
        padding-top: 10px;
        padding-bottom: 30px;
        margin:10px;
        border-radius: 50px;
        outline: white solid 2px;
        outline-offset: -20px;
    }
</style>
