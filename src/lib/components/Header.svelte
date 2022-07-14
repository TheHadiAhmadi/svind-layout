<script>
import { getContext, onDestroy, onMount } from "svelte";

import Navbar from "./Navbar.svelte";

let className = '';
export {className as class}

export let height = 80;

const layout = getContext('layout')

onMount(() => {
    layout.registerHeader()
})


onDestroy(() => {
    layout.removeHeader()
})

$: fixed = layout.fixed;

 
</script>
<Navbar {height} class={className} fixed={$fixed}>
    <slot/>
</Navbar>