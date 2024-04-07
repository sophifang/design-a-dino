<script>
  import Dinodex from "./Dinodex.svelte";
  import DesignADino from "./Design-A-Dino.svelte";
  import DinoTrends from "./DinoTrends.svelte";
  let page = "design-a-dino"
  function change_page(new_page){
    if (new_page == "dinodex"){
      page = "dinodex"
    } else if (new_page == "dinoTrends"){
      page = "dinoTrends"
    } else{
      page = "design-a-dino"
    }
  }
</script>

<main>
  <div class="container">
    <div class="navBar">
      <div class="pages">
        <button class="pageButton" on:click={() => change_page("design-a-dino")}> Design-A-Dino </button>
        <button class="pageButton" on:click={() => change_page("dinodex")}> Dinodex </button>
        <button class="pageButton" on:click={() => change_page("dinoTrends")}> DinoTrends </button>

      </div>
    </div>
  </div>

  {#if page == "design-a-dino"}
    <DesignADino/>  
  {:else if page == "dinodex"}
    <Dinodex/>
    {:else if page == "dinoTrends"}
    <DinoTrends/>
  {/if}

</main>

<style>
  main {
    font-family: 'Quicksand';
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
    padding-right:3%
  }
  button:hover {
    background-color: #002A84;
  }

  .container {
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
  }

  .container>div.navBar {
    display: flex;
    position: fixed;
    align-items: center;
    justify-content: flex-start;
    flex-direction: column;
    width: 100%;
    height: 55px;
    background-color: #003d73;
    z-index: 10;
  }

  .pages {
    width: 100%;
    height: 100%;
  }

  button.pageButton {
    margin-top: 5px;
    scale: 0.8;
  }
  

  .logo{
    width: 100%;
    height: 100%;
    scale:0.1;
  }
  
</style>
