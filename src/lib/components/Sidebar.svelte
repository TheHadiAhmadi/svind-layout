<script>
	import { getContext, onDestroy, onMount } from 'svelte';

	import Navbar from './Navbar.svelte';

    /** @type {'compact'|'icon'|'default'}*/
    export let mode = 'default';
	export let width = 0;

	export let fixed = false

	const {sidebarWidth, hasSidebar, hasHeader, hasFooter} =  getContext('layout')

	onMount(() => {
		$hasSidebar = true
	})
	
	onDestroy(() => {
		$hasSidebar = false
	})
	

	$: style= [
		$hasHeader !== 'full' ? "; --header-height: 0" : '',
		$hasFooter !== 'full' ? "; --footer-height: 0" : '',
		fixed && $hasFooter === 'full' ? "; --footer-height: 0" : '',
	].join(';')
	$: $sidebarWidth = width;
</script>


<Navbar {fixed} style="bottom: var(--footer-height); top: var(--header-height); width: var(--sidebar-width); {style}" vertical class="sidebar-{mode}">
	<slot />
</Navbar>
