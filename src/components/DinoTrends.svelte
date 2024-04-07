<script>
    import { onMount } from "svelte";
    import * as d3 from 'd3';

    let dinos = [];
    let cur_alpha = "A";
    let new_alpha = "A";
    let filter_type = "All";
    let filter;
    let diet;
    let type;
    let all;
    let img_src = "all_dinos.html";

    onMount(async () => {
        const res = await fetch('dinos.csv'); 
        const csv = await res.text();
        dinos = d3.csvParse(csv, d3.autoType)
        var filter_type = document.getElementById("filters").value;
        console.log(dinos[0]["name"]);
    });

    function check_alpha(alpha){
        new_alpha = alpha;
        if(cur_alpha != new_alpha){
            cur_alpha = alpha;
            return true
        }
        return false
    }

    $: console.log(img_src)
	
	const onChange = () => {
		if (filter_type == "All"){
            img_src = "all_dinos.html";
        } else if(filter_type == "Diet"){
            if (diet == "Carnivorous"){
                img_src = "carnivorous_dinos.html";
            } else if(diet == "Herbivorous"){
                img_src = "herbivorous_dinos.html";
            } else if(diet == "Omnivorous"){
                img_src = "omnivorous_dinos.html";
            }
        } else if(filter_type == "Type"){
            if (type == "sauropod"){
                img_src = "sauropods.html";
            } else if(type == "theropod"){
                img_src = "theropods.html";
            } else if(type == "ceratopsian"){
                img_src = "ceratopsians.html";
            } else if(type == "euornithopod"){
                img_src = "euornithopods.html";
            } else if(type == "armoured dinosaur"){
                img_src = "armoured_dinosaurs.html";
            }
        }
	}



</script>

<main>
    <!-- Dino Locations -->
    <div class = "trends">
        <div class="section">
            <h1 class="title">
                Discover More On Dinos!
            </h1>
            <h3 class="subtitle">
                Hover over regions on the world map to learn more.
            </h3>
            <iframe class="map" src={img_src} width=800 height=490 frameBorder=0></iframe>

            <label for="filters">Pick a filter:</label>
            <select class="filters" id="filters" bind:value={filter_type} on:change={onChange}>
                <option value={"All"}>All</option>
                <option value={"Diet"}>Diet</option>
                <option value={"Type"}>Type</option>
            </select>
            <br/>

            {#if filter_type == "Diet"}
                <label for="filters">Pick a diet:</label>
                <select class="filters" id="filters" bind:value={diet} on:change={onChange}>
                    <option value={"Carnivorous"}>Carnivorous</option>
                    <option value={"Herbivorous"}>Herbivorous</option>
                    <option value={"Omnivorous"}>Omnivorous</option>
                </select>
            {:else if filter_type == "Type"}
                <label for="filters">Pick a type:</label>
                <select class="filters" id="filters" bind:value={type} on:change={onChange}>
                    <option value={"sauropod"}>Sauropods</option>
                    <option value={"theropod"}>Theropods</option>
                    <option value={"ceratopsian"}>Ceratopsians</option>
                    <option value={"euornithopod"}>Euornithopods</option>
                    <option value={"armoured dinosaur"}>Armoured Dinosaurs</option>
                </select>
            {/if}

        </div>
    </div>
</main>

<style>
    main {
        font-family: 'Quicksand';
    }

    
    .trends {
        width: 100%;
        height: 700px;
        /* background-attachment: fixed; */
        text-align: center;
    }

    .section{
        background-color: white;
        text-align: center;
        align-items: center;

        border-radius: 15px;
        margin-top: 5%;
        margin-left: 15%;
        margin-right: 15%;
    }

    .title{
        background-color:#F5F5F5;
        border-radius: 25px;
        padding-top: 1%;
        padding-bottom: 1%;
        margin-left: 10%;
        margin-right: 10%;
        margin-bottom: 0%;
        transform: translateY(-50%);
    }

    .subtitle{
        margin-top: 0%;
        margin-bottom: 0%;
    }


    .section .map {
        margin-left: 14%;
        display: block;
    }

    .filters{
        margin-bottom: 2%;
    }

</style>