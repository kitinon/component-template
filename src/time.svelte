<svelte:options tag="s-time"/>

<script>
  import { onMount } from 'svelte'
  let time = now()

  function now() {
    const d = new Date()
    const h = d.getHours()
    const mm = d.getMinutes().toString().padStart(2, '0')
    const ss = d.getSeconds().toString().padStart(2, '0')
    return h + ':' + mm + ':' + ss
  }
  onMount(() => {
    const interval = setInterval(()=>time=now(), 1000)
    return ()=>clearInterval(interval)
  })
</script>

<div>
  {time}
</div>