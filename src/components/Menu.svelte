<script>
    export let types;
      export let selectedType;
  </script>

  <section class="menu-cont">
      <select class="menu" 
                      name="menu" 
                      id="menu" 
                      bind:value={selectedType}>
          <option disabled selected value="">Select a type.</option>
          <option value="all">All type</option>
          {#each types as type}
              <option value={type}>{type}</option>
          {/each}
      </select>
  </section>
  
  
  <style>
      .menu-cont {
          width: 40%;
          display: flex;
          margin: 0 10px 0 0;
      }
      
      select {
          margin: 0;
          font-size: 1.18rem;
          border: 1px solid gray;
          border-radius: 5px;
      }
      
      .menu {
          width: 100%
      }
  </style>