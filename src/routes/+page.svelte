<script>
    let maxClick = $state(0);
    let cnt = $state(0); // tip: https://svelte.dev/docs/svelte/$state
    
  
    function onClick() {
      // tip: Since DOM (i.e., the webpage content) will automatically update based on values, [<p id="info">Remaining Number of Clicks: {cnt}</p>]
      // we only need to change the cnt number here. 
      if(cnt>0)cnt--;
    }
  </script>
  
  <h1>Harry Lu's VIS Site</h1>
  <img
    width="200px"
    src="/harrylu_avatar.jpg"
    alt="Site Favicon"
  />
  <div>
    You can click up to
    <select 
        bind:value={maxClick}
        onchange={(event) => {
            cnt = maxClick;
        }}
    >
      {#each [2, 4, 6] as optionNum}
        <option value={optionNum}>
          {optionNum}
        </option>
      {/each}
    </select>
    times
  </div>
  <button onclick={onClick}> Click Me </button>

  <!-- tip: use {#if...} template syntax here (https://svelte.dev/docs/svelte/if) so that the content below will automatically update when cnt value changes -->
    <!-- `the content below should only show when cnt >0` -->
    {#if cnt>0}
    <p id="info">Remaining Number of Clicks: {cnt}</p>
    <!-- The content below should only shown when cnt =0 -->
    {:else if cnt==0}
    <p>No more clicks allowed</p>
    {/if}
  
  
  <style>
    button {
      background-color: #44aa66;
      /* background-color: blue; */
      color: white;
      font-size: xx-large;
      padding: 10px 20px;
      border: none;
      cursor: pointer;
      border-radius: 5px;
    }
  </style>
  