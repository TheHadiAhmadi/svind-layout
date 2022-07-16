<script>
    export let open = false;
    export let width = 200;
</script>
<div style="width: {width }px; right: -{width}px" class="d-drawer" class:open>
    <slot/>
</div>

<style global>
    	.d-drawer {
		padding: 16px;
		position: fixed;
		overflow: auto;
		/* right: -240px; */
		/* width: 240px; */
		opacity: 0.5;
		top: 0;
		bottom: 0;
		z-index: 3;
		background-color: white;
		transition: all 0.3s ease; 
	}
	.d-drawer.open {
		right: 0 !important;
		opacity: 1;
		box-shadow: -2px 0 6px -4px  black;
	}
	.dark .d-drawer {
		background-color: #303030;
	}
</style>