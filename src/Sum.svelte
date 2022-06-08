<script lang="ts">
  export{}
  import counters from "./App.svelte";
  export let total: any;
  function sumCount () {
    total = (counters as any).reduce((tanaka: any, kimura: any) => tanaka + kimura.counts, 0);
  }
</script>


<button class="btn" on:click={sumCount}>合計を計算</button>
Sum: {total}

