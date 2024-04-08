<script>
    import { onMount } from "svelte";
    import * as d3 from 'd3';
    let data = [];

    onMount(async () => {
        const res = await fetch('dinodata.csv'); 
        const csv = await res.text();
        data = d3.csvParse(csv, d3.autoType)
        console.log(data);
    });
    let page = 0;
    let diet;
    let region;
    let type;
    let length;
    let name;
    let imgNum = 0;
    function next() {
        page++;
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
    let filteredDinosDiet = [];
    function selectDiet(selectedDiet) {
        diet = selectedDiet;
        for (let dinoObj of data) {
            if (dinoObj.diet === diet) {
                filteredDinosDiet = [...filteredDinosDiet, dinoObj]
            }
        }
        console.log(filteredDinosDiet)
    }
    let filteredDinosRegion = [];
    function selectRegion(selectedRegion) {
        region = selectedRegion;
        for (let dinoObj of filteredDinosDiet) {
            if (dinoObj.continent === region) {
                filteredDinosRegion = [...filteredDinosRegion, dinoObj]
            }
        }
        console.log(filteredDinosRegion)
    }
    let filteredDinosType = [];
    function selectType(selectedType) {
        type = selectedType;
        for (let dinoObj of filteredDinosRegion) {
            if (dinoObj.type === type) {
                filteredDinosType = [...filteredDinosType, dinoObj]
            }
        }
        console.log(filteredDinosType)
    }
    let chosenDino;
    let filteredDinosLength= [];
    function selectLength(selectedLength) {
        length = selectedLength;
        for (let dinoObj of filteredDinosType) {
            if (dinoObj.size === length) {
                filteredDinosLength = [...filteredDinosLength, dinoObj]
            }
        }
        console.log(filteredDinosLength)

        if (filteredDinosLength.length > 0) {
            chosenDino = filteredDinosLength[Math.floor(Math.random() * filteredDinosLength.length)];
            console.log(chosenDino);
        } else if (filteredDinosType.length > 0) {
            chosenDino = filteredDinosType[Math.floor(Math.random() * filteredDinosType.length)];

        } else if (filteredDinosRegion > 0) {
            chosenDino = filteredDinosRegion[Math.floor(Math.random() * filteredDinosRegion.length)];
        } else {
            chosenDino = filteredDinosDiet[Math.floor(Math.random() * filteredDinosDiet.length)];
        }
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
                <div class = "column" on:click={() => selectDiet("Herbivorous")} style={`border: solid 2px ${diet === "Herbivorous" ? "#D9D9D9" : "#fff"}; background-color: ${diet === "Herbivorous" ? "#f5f5f5" : "#fff"}`}>
                <h3>Herbivore</h3>
                <img class = "icon" src = "herbivore.png"/>
                </div>
                <div class = "column" on:click={() => selectDiet("Carnivorous")} style={`border: solid 2px ${diet === "Carnivorous" ? "#D9D9D9" : "#fff"}; background-color: ${diet === "Carnivorous" ? "#f5f5f5" : "#fff"}`}>
                <h3>Carnivore</h3>
                <img class = "icon" src = "carnivore.png"/>
                </div>
                <div class = "column" on:click={() => selectDiet("Omnivorous")} style={`border: solid 2px ${diet === "Omnivorous" ? "#D9D9D9" : "#fff"}; background-color: ${diet === "Omnivorous" ? "#f5f5f5" : "#fff"}`}>
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
                <div class = "column" on:click={() => selectRegion("Asia")} style={`border: solid 2px ${region === "Asia" ? "#D9D9D9" : "#fff"}; background-color: ${region === "Asia" ? "#f5f5f5" : "#fff"}`}>
                <h3>Asia</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("Africa")} style={`border: solid 2px ${region === "Africa" ? "#D9D9D9" : "#fff"}; background-color: ${region === "Africa" ? "#f5f5f5" : "#fff"}`}>
                <h3>Africa</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("North America")} style={`border: solid 2px ${region === "North America" ? "#D9D9D9" : "#fff"}; background-color: ${region === "North America" ? "#f5f5f5" : "#fff"}`}>
                <h3>North America</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("South America")} style={`border: solid 2px ${region === "South America" ? "#D9D9D9" : "#fff"}; background-color: ${region === "South America" ? "#f5f5f5" : "#fff"}`}>
                <h3>South America</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("Antartica")} style={`border: solid 2px ${region === "Antartica" ? "#D9D9D9" : "#fff"}; background-color: ${region === "Antartica" ? "#f5f5f5" : "#fff"}`}>
                <h3>Antartica</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("Europe")} style={`border: solid 2px ${region === "Europe" ? "#D9D9D9" : "#fff"}; background-color: ${region === "Europe" ? "#f5f5f5" : "#fff"}`}>
                <h3>Europe</h3>
                </div>
                <div class = "column" on:click={() => selectRegion("Oceania")} style={`border: solid 2px ${region === "Oceania" ? "#D9D9D9" : "#fff"}; background-color: ${region === "Oceania" ? "#f5f5f5" : "#fff"}`}>
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
                    <div class = "column" on:click={() => selectType("Sauropod")} style={`border: solid 2px ${type === "Sauropod" ? "#D9D9D9" : "#fff"}; background-color: ${type === "Sauropod" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "sauropod.png"/>
                        <h3>Sauropod</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 1}
                    <div class = "column" on:click={() => selectType("Ceratopsian")} style={`border: solid 2px ${type === "Ceratopsian" ? "#D9D9D9" : "#fff"}; background-color: ${type === "Ceratopsian" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "ceratopsian.png"/>
                        <h3>Ceratopsian</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 2}
                    <div class = "column" on:click={() => selectType("Euornithopod")} style={`border: solid 2px ${type === "Euornithopod" ? "#D9D9D9" : "#fff"}; background-color: ${type === "Euornithopod" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "euornithopod.png"/>
                        <h3>Euornithopod</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 3}
                    <div class = "column" on:click={() => selectType("Small Theropod")} style={`border: solid 2px ${type === "Small Theropod" ? "#D9D9D9" : "#fff"}; background-color: ${type === "Small Theropod" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "small-theropod.png"/>
                        <h3>Small Theropod</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 4}
                    <div class = "column" on:click={() => selectType("Large Theropod")} style={`border: solid 2px ${type === "Large Theropod" ? "#D9D9D9" : "#fff"}; background-color: ${type === "Large Theropod" ? "#f5f5f5" : "#fff"}`}>
                        <img class = "icon" src = "large-theropod.png"/>
                        <h3>Large Theropod</h3>
                    </div>
                {/if}
                {#if imgNum % 6 === 5}
                    <div class = "column" on:click={() => selectType("Armoured Dinosaur")} style={`border: solid 2px ${type === "Armoured Dinosaur" ? "#D9D9D9" : "#fff"}; background-color: ${type === "Armoured Dinosaur" ? "#f5f5f5" : "#fff"}`}>
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
                <div class = "column" on:click={() => selectLength("Short")} style={`border: solid 2px ${length === "Short" ? "#D9D9D9" : "#fff"}; background-color: ${length === "Short" ? "#f5f5f5" : "#fff"}`}>
                    <h3>Short</h3>
                    <img class = "icon" src = "short.png"/>
                </div>
                <div class = "column" on:click={() => selectLength("Medium")} style={`border: solid 2px ${length === "Medium" ? "#D9D9D9" : "#fff"}; background-color: ${length === "Medium" ? "#f5f5f5" : "#fff"}`}>
                    <h3>Medium</h3>
                    <img class = "icon" src = "medium.png"/>
                </div>
                <div class = "column" on:click={() => selectLength("Long")} style={`border: solid 2px ${length === "Long" ? "#D9D9D9" : "#fff"}; background-color: ${length === "Long" ? "#f5f5f5" : "#fff"}`}>
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
            <div class = "row">
                <div class = "column">
                    <img class = "icon" src={"https://www.nhm.ac.uk/resources/nature-online/life/dinosaurs/dinosaur-directory/images/reconstruction/small/".concat(chosenDino.name).concat(".jpg")}/>
                </div>
                <div class = "column">
                    <p>{name} is a(n) {chosenDino.name}, which is a type of {chosenDino.type}. {name} lived during the {chosenDino.period_time} {chosenDino.period} period in {chosenDino.continent} and was {chosenDino.diet}. It was approximately {chosenDino.length} meters long.</p>
                </div>
            </div>
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
        margin-top: 170px;
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
    .dino-fact .question-box {
        padding: 0;
        height: 300px;
        margin-top: 230px;
    }
    .dino-fact p {
        font-size: 20px;
    }
    .dino-fact .row {
        height: 150px;
        margin-top: 150px;
    }
    .dino-fact .column:hover {
        background-color: transparent;
        border-radius: 0%;
        outline: 0px;
        outline-offset: 0px;
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
        width: 70%;
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
