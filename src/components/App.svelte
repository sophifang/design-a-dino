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

        <!-- <div class="logo">
          <img src="logo.png"/>
        </div> -->
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
  .background {
    width: 100%;
    height: auto;
    background-attachment: fixed;
    /* z-index: -1;
    position: absolute; */
  }
  .page {
    /* display: flex;
    justify-content: center; */
    
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
  }
  .column:hover {
    background-color: #F5F5F5;
    border-radius: 15%;
    outline: 2px solid #D9D9D9;
    outline-offset: 0px;
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
    height: 50px;
    background-color: #003d73;
    z-index: 10;
  }

  .pages {
    width: 100%;
    height: 100%;
    margin-left: 20px;
  }

  button.pageButton {
    scale: 0.8;
  }
  

  .logo{
    width: 100%;
    height: 100%;
    scale:0.1;
  }
  
</style>
