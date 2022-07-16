<script>
	import { setContext } from 'svelte';
	import { writable } from 'svelte/store';

	const sidebarWidth = writable(240)
	const headerHeight = writable(80)
	const footerHeight = writable(64)
	const hasHeader = writable(false)
	const hasSidebar = writable(false)
	const hasFooter = writable(false)

	export let fixed = false;
	export let dark = false;

	const fixedStore = writable(fixed);

	$: $fixedStore = fixed;
	setContext('layout', {
		sidebarWidth,
		footerHeight,
		headerHeight,
		fixed: fixedStore,
		hasHeader,
		hasSidebar,
		hasFooter,
	});
	$: console.log($hasSidebar)

	$: console.log($footerHeight, $hasFooter)
	$: console.log($headerHeight, $hasHeader)
	$: console.log($sidebarWidth, $hasSidebar)
	$: style = [
		`--header-height: ${$hasHeader ? $headerHeight : 0}px`,
		`--footer-height: ${$hasFooter ? $footerHeight : 0}px`,
		`--sidebar-width: ${$hasSidebar ? $sidebarWidth : 0}px`
	].join(';\n');
</script>

<div class="d-page" {style} class:dark>
	<slot />
</div>

<style global>
	.d-page {
		position: relative;
		overflow: hidden;
		width: 100%;
		min-height: 100vh;
		background-color: #efefef;
	}
</style>
