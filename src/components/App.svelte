<script>
  // Write your JS here, or import other files
</script>

<main>
  <!-- home -->
  <div>
    <img class = "background" src = "dino-home.png"/>
    <button>LET'S GO!</button>
  </div>
  <!-- Dino Diet -->
  <div class = "page">
    <img class = "background" src="dino-question.png"/>
    <div class = "question-box">
      <h2>Dino Diet</h2>
      <div class = "row">
        <div class = "column">
          <h3>Herbivore</h3>
          <img class = "icon" src = "herbivore.png"/>
        </div>
        <div class = "column">
          <h3>Carnivore</h3>
          <img class = "icon" src = "carnivore.png"/>
        </div>
        <div class = "column">
          <h3>Omnivore</h3>
          <img class = "icon" src = "omnivore.png"/>
        </div>
      </div>
      <button>NEXT</button>
    </div>
  </div>

  <!-- Dino Region -->
  <div class = "region">
    <img class = "background" src="dino-question.png"/>
    <div class = "question-box">
      <h2>Dino Region</h2>
      <div class = "row">
        <div class = "column">
          <h3>Asia</h3>
        </div>
        <div class = "column">
          <h3>Africa</h3>
        </div>
        <div class = "column">
          <h3>North America</h3>
        </div>
        <div class = "column">
          <h3>South America</h3>
        </div>
        <div class = "column">
          <h3>Antartica</h3>
        </div>
        <div class = "column">
          <h3>Europe</h3>
        </div>
        <div class = "column">
          <h3>Oceania</h3>
        </div>
      </div>
      <button>NEXT</button>
    </div>
  </div>

  <!-- Dino Type -->
  <div class = "page">
    <img class = "background" src="dino-question.png"/>
    <div class = "question-box">
      <h2>Dino Diet</h2>
      <div class = "row">
        <div>
          <img class = "icon" src = "left-arrow.png"/>
        </div>
        <div class = "column">
          <img class = "icon" src = "sauropod.png"/>
          <h3>Sauropod</h3>
        </div>
        <div>
          <img class = "icon" src = "right-arrow.png"/>
        </div>
      </div>
      <button>NEXT</button>
    </div>
  </div>

  <!-- Dino Type -->
  <div class = "page">
    <img class = "background" src="dino-question.png"/>
    <div class = "question-box">
      <h2>Dino Type</h2>
      <div class = "row">
        <div class = "column">
          <h3>Short</h3>
          <img class = "icon" src = "short.png"/>
        </div>
        <div class = "column">
          <h3>Medium</h3>
          <img class = "icon" src = "medium.png"/>
        </div>
        <div class = "column">
          <h3>Long</h3>
          <img class = "icon" src = "long.png"/>
        </div>
      </div>
      <button>NEXT</button>
    </div>
  </div>

  <!-- Dino Name -->
    <div class = "page">
      <img class = "background" src="dino-question.png"/>
      <div class = "question-box">
        <h2>Dino Name</h2>
        <div class = "row">
          <div>
            <img class = "icon" src = "name.png"/>
            <input>
          </div>
        </div>
        <button>GENERATE DINO!</button>
      </div>
    </div>
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
