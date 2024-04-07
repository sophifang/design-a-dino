<script>
	export let searchTerm;
</script>


<div>
	<input type="text" placeholder="Enter Search Term" bind:value={searchTerm} on:input />
</div> 


<style>
	div {
		width: 40%;
		display: flex;
		align-items: center;
		margin: 0 0 0 10px;
	}

	input {
        font-family: 'Quicksand';
		width: 100%;
		font-size: 20px;
		border: 1px solid gray;
		border-radius: 5px;
		padding: 5px;
	}

</style>