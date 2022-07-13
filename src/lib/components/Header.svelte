<script>
import { getContext, onMount } from "svelte";

import Navbar from "./Navbar.svelte";

const layout = getContext('layout')

layout.registerHeader()

$: fixed = layout.fixed;
 
</script>
<Navbar fixed={$fixed}>
    <slot/>
</Navbar>