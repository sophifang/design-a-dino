<script>
    export let types;
    export let selectedType;
  </script>

  <main>
      <select bind:value={selectedType}>
          <option disabled selected value="">Select a type.</option>
          <option value="all">All types</option>
          {#each types as type}
              <option value={type}>{type}</option>
          {/each}
      </select>
    </main>
  
  
  <style>
      main {
        width: 30%;
        display: flex;
        margin: 0 100px 0 0;
      }
      
      select {
        font-family: 'Quicksand';
        margin: 0;
        font-size: 20px;
        border: 1px solid gray;
        border-radius: 5px;
        padding: 5px;
      }
  </style>