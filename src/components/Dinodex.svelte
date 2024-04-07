<script>
    import { onMount } from "svelte";
    import * as d3 from 'd3';

    let dinos = [];
    let cur_alpha = "A";
    let new_alpha = "A";

    onMount(async () => {
        const res = await fetch('dinodata.csv'); 
        const csv = await res.text();
        dinos = d3.csvParse(csv, d3.autoType)

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
</script>

<main>
    <!-- Dino Info -->
    {#each dinos as d, i}
    <br/>
    {#if check_alpha(d["name"][0])}
        <h2> {d["name"][0].toUpperCase()} </h2>
    {/if}
    <button>{d["name"]}</button>
    {/each}
</main>

<style>
    
</style>