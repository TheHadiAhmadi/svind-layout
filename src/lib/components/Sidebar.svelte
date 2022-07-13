<script>
	import { getContext, onMount } from 'svelte';

	import Navbar from './Navbar.svelte';

    /** @type {'compact'|'icon'|'default'}*/
    export let mode = 'default';

	const layout = getContext('layout');
    

    $: fixed = layout.fixed

	$: layout.registerSidebar(mode);
</script>

<Navbar vertical fixed={$fixed} class="sidebar-{mode}">
	<slot />
</Navbar>
