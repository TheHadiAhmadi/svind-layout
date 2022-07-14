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

    function removeSidebar() {
        hasSidebar = null
    }
    function removeHeader() {
        hasHeader = null
    }

    const fixedStore = writable(fixed)
	const sidebarWidth = writable(240)
	const headerHeight = writable(80)

    $: $fixedStore = fixed
	setContext('layout', { removeSidebar, removeHeader, registerHeader, registerSidebar, fixed: fixedStore });
</script>

<div class="d-page" class:dark data-layout-sidebar={hasSidebar} data-layout-header={hasHeader}>
	<slot {sidebarWidth} {headerHeight} />
</div>
