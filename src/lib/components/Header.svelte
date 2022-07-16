<script>
	import { getContext, onDestroy, onMount } from 'svelte';

	import Navbar from './Navbar.svelte';

	const {hasHeader, headerHeight} = getContext('layout');

	let className = '';
	export { className as class };

	export let height = 0;
    export let fixed = false;
    export let fullWidth = false;


	onMount(() => {
        $hasHeader = true
	});
    
    
	onDestroy(() => {
        $hasHeader = false
	});
    
    $: $headerHeight = height
    $: $hasHeader = fullWidth ? 'full' : true

</script>

<Navbar class="{className} {fullWidth ? ' full ': ''}" {fixed}>
	<slot />
</Navbar>

<style global>
    .d-navbar:not(.vertical) {
        z-index: 2;
        height: var(--header-height);
        left: var(--sidebar-width);
    }

    .d-navbar:not(.vertical).full {
        left: 0;
    }
    

</style>
