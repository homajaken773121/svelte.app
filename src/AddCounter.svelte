<script lang="ts">
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    let counter = {
      id: 0,
      title: "",
      counts: 0
    };
    const onSubmit = (e: any) => {
      e.preventDefault();
      let randomId = Math.random(); //カウンターをユニークなものにするため乱数IDをつける
      dispatch("addcounter", counter);
      counter = {
        id: randomId,
        title: "",
        counts: 0
      };
    };
</script>
  
<form on:submit={onSubmit} class="grid-3">
  <input type="text" placeholder="Counter Name" bind:value={counter.title} required/>
  <input type="submit" class="btn btn-primary" value="Add Counter" />
</form>