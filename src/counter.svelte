<script lang="ts">
    export{}
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    export let id: any;
    export let title: any;
    export let counts: any;
    
    //カウントと削除
    const addCount = (): number => (counts += 1);
    const removeCount = (): number => (counts -= 1);
    const reset = (): number => (counts = 0);
    const onDelete = (): boolean => dispatch("removecounter", id);
    

</script>


<div class="card">
  <h3>
    <input  type="text" placeholder="counter title" bind:value={title}>
    <button class="btn" on:click={addCount}>+1</button>
    <button class="btn btn-dark" on:click={removeCount}>-1</button>
    <button class="btn" on:click={reset}>reset</button>
    <button class="btn btn-danger btn-sm" on:click={onDelete}>削除</button>
    
    Counts: {counts}
  </h3>
</div>


<style>
  h3 {
    color: #204f6e;
    margin-bottom: 10px;
  }
</style>

