<script>
import { getContext, onDestroy, onMount } from "svelte";

import Navbar from "./Navbar.svelte";

const layout = getContext('layout')

onMount(() => {
    layout.registerHeader()
})


onDestroy(() => {
    layout.removeHeader()
})

$: fixed = layout.fixed;

 
</script>
<Navbar fixed={$fixed}>
    <slot/>
</Navbar>