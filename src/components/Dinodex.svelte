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
        console.log("dinos", dinos);
        getTypes();
    });
	let types = [];
	let selectedType = "";	
	console.log("dinos", dinos);
	const getTypes = () => {
		for (let dinoObj of dinos) {
            console.log(dinoObj);
			if (!types.includes(dinoObj.type)) {
				types = [...types, dinoObj.type]
			}
		}
		types = types.sort();
	}	
	
	
	// Query results
	let filteredDinos = [];
	
	// For Select Menu
	$: if (selectedType) getDinosByType();
	$: console.log(filteredDinos, selectedType);
	
	const getDinosByType = () => {
		searchTerm = ""; 
		
		if (selectedType === "all") {
			return filteredDinos = [];
		} 
		return filteredDinos = dinos.filter(dino => dino.type === selectedType);

	}	
	
	// For Search Input
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
<section id="query-section">
	<Menu {types} bind:selectedType />
	<Search bind:searchTerm on:input={searchDinos} />
</section>
<main id="bookshelf">
    {#if filteredDinos.length > 0}
        {#each filteredDinos as {name, type}}
            <Dino {name}{type}/>
        {/each}	
    {:else}
        {#each dinos as {name, type}}
            <Dino {name}{type}/>
        {/each}	
    {/if}
</main>

<style>
    * {
		box-sizing: border-box;
	}
    #query-section {
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 2% 0;
	}
	/* General Structure */
	main#bookshelf {
		width: 100%;
		margin: 10px;
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		align-items: flex-start;
		justify-content: center; 
	}
</style>