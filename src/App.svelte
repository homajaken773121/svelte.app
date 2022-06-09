<svelte:head>
  <link rel="stylesheet" href="https://raw.githack.com/bradtraversy/svelte-scoreboard/master/public/global.css">
</svelte:head>

<script lang="ts">
  export{}
  import Navbar from "./Navbar.svelte";
  import Counter from "./counter.svelte";
  import AddCounter from "./AddCounter.svelte";
  import Sum from "./Sum.svelte";
  
  let counters = [];

  let total: any;
  
  const addCounter = (e: any) => {
    const newCounter = e.detail;
    counters = [...counters, newCounter];
    alert( "配列のサイズは" + Object.keys( counters ).length );
  };
  
  const removeCounter = (e: any) => {
    counters = counters.filter(counter => counter.id !== e.detail);
  };
  
</script>


<Navbar />
<div class="container">
  <Sum {total}/>
</div>

<div class="container">
  <AddCounter on:addcounter={addCounter} />
  {#if counters.length === 0}
    <p>No Counters</p>
  {:else}
    {#each counters as counter}
      <Counter
	  	  id={counter.id}
        title={counter.title}
        counts={counter.counts}
        on:removecounter={removeCounter}
      />
    {/each}
  {/if}
</div>