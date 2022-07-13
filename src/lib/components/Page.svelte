<script>
	import { setContext } from 'svelte';
import { writable } from 'svelte/store';

	let hasHeader = null;
	let hasSidebar = null;
    export let fixed = false;
    export let dark = false;

	function registerHeader() {
		hasHeader = true;
	}
	function registerSidebar(mode) {
		hasSidebar = mode;
	}

    const fixedStore = writable(fixed)

    $: $fixedStore = fixed
	setContext('layout', { registerHeader, registerSidebar, fixed: fixedStore });
</script>

<div class="d-page" class:dark data-layout-sidebar={hasSidebar} data-layout-header={hasHeader}>
	<slot />
</div>
