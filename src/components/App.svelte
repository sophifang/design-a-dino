<script>
  import Dinodex from "./Dinodex.svelte";
  import DesignADino from "./Design-A-Dino.svelte";

  let page = "dinodex"

  function toggle(){
    if (page == "design-a-dino"){
      page = "dinodex"
    } else{
      page = "design-a-dino"
    }
  }
</script>

<main>

  
  {#if page == "design-a-dino"}
    <DesignADino/>  
  {:else}
    <Dinodex/>
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
</style>
