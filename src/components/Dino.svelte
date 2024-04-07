<script>
	export let name;
	export let type;
</script>


<section class="book">
	
	<section class="book-top-info">
		<figure class="bkcont">
			<img src={"https://www.nhm.ac.uk/resources/nature-online/life/dinosaurs/dinosaur-directory/images/reconstruction/small/".concat(name).concat(".jpg")} alt={name} class="bkcover">
			<figcaption>{name}</figcaption>
            <div class="language">{type}</div>
		</figure>
	</section> 
	
</section>


<style>
	.book { 
			width: 280px;
			border-radius: 3px;
			margin: 5px;
		}

		.book-top-info {
			width: 100%;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: flex-start;
		}

		/* Book Layout */
		.bkcont {
			width: 100%;
			text-align: center;
		}

		.bkcover {
			width: 200px;
			height: 150px;
		}
	
		div.language {
			font-size: .8em;
			margin: 5px 0;
		}
	
		figcaption {
			text-align: center;
			width: 90%;
			padding: 3px 10px;
			height: 36px;
			font-weight: bold;
		}
	
</style>