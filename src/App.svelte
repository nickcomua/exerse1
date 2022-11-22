<script>
  import Comp from './component.svelte' 
  import { Alert, Input , Button } from 'sveltestrap'; 
  let flags = []
  let msgs = []
  let logs = [] 
  var n = 2 
  $: if (msgs.some(x => x != null)) {msgs.forEach(x =>  x ? logs=[...logs,x]:{});msgs=[]}
  let inc = () =>{flags = flags.map(x => true)};
</script> 
<Input type='number' bind:value={n}/> <br>

{#each [...Array(n).keys()] as i}
<Comp  bind:flag = {flags[i]} on:click = {inc} bind:msg={msgs[i]}/> 
<br>
{/each}
<Button on:click = {() => {logs = []}}>clear all</Button>
<br><br>
{#each logs as i}
<Alert color="{i[0]?'success':'danger'}" dismissible>
  {i[1]}
</Alert> 
{/each} 