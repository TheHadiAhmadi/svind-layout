<script>
	import { getContext, onDestroy, onMount } from 'svelte';

	import Navbar from './Navbar.svelte';

    /** @type {'compact'|'icon'|'default'}*/
    export let mode = 'default';

	export let width = 240;
	export let top = 80;

	const layout = getContext('layout');
    

    $: fixed = layout.fixed

	$: layout.registerSidebar(mode);

onDestroy(() => {
    layout.removeSidebar()
})

</script>

<Navbar {width} {top} vertical fixed={$fixed} class="sidebar-{mode}">
	<slot />
</Navbar>
