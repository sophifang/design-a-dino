<script>
    import { onMount } from "svelte";
    import * as d3 from 'd3';
    import Dino from './Dino.svelte';
	import Menu from './Menu.svelte';
	import Search from './Search.svelte';
    let dinos = [];

    onMount(async () => {
        const res = await fetch('dinodata.csv'); 
        const csv = await res.text();
        dinos = d3.csvParse(csv, d3.autoType);
        getTypes();
    });
	let types = [];
	let selectedType = "";	

	const getTypes = () => {
		for (let dinoObj of dinos) {
            console.log(dinoObj);
			if (!types.includes(dinoObj.type)) {
				types = [...types, dinoObj.type]
			}
		}
		types = types.sort();
	}	
	
	let filteredDinos = [];

	$: if (selectedType) getDinosByType();
	$: console.log(filteredDinos, selectedType);
	
	const getDinosByType = () => {
		searchTerm = ""; 
		
		if (selectedType === "all") {
			return filteredDinos = [];
		} 
		return filteredDinos = dinos.filter(dino => dino.type === selectedType);

	}	
	
	let searchTerm = "";
	$: if (searchTerm) selectedType = ""; 
	
	const searchDinos = () => {	
		return filteredDinos = dinos.filter(dino => {
			let dinoName = dino.name.toLowerCase();
			return dinoName.includes(searchTerm.toLowerCase())
		});
	}
    console.log(filteredDinos);
</script>

<main>
    <div class="nav">
        <Menu {types} bind:selectedType />
        <Search bind:searchTerm on:input={searchDinos} />
    </div>
    <div class = "grid">
        {#if filteredDinos.length > 0}
        {#each filteredDinos as {name, type}}
            <Dino {name}{type}/>
        {/each}	
        {:else}
            {#each dinos as {name, type}}
                <Dino {name}{type}/>
            {/each}	
        {/if}
    </div>
</main>

<style>
    main {
		box-sizing: border-box;
	}
    .nav {
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 2% 0;
	}
	.grid {
		width: 100%;
		margin: 10px;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		align-items: flex-start;
		justify-content: center; 
	}
</style>