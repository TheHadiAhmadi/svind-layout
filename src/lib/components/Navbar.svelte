<script>
    export let vertical  = false
    export let fixed = false;
    export let open = false;
   
    let className= ''
    export {className as class}; 

    export let style= '';

    // $: styleTop =  top > 0 ? `top: ${top}px;` : ''
    // $: styleBottom =  bottom > 0 ? `bottom: ${bottom}px;` : ''
    // $: styleWidth =  width > 0 ? `width: ${width}px;` : ''
    // $: styleHeight = height > 0 ? `height: ${height}px;` : ''
    // $: styles = styleTop + styleBottom + styleWidth + styleHeight + style
</script>
<nav {style} class:open class:vertical class="{className} d-navbar" class:fixed>
    <slot/>
</nav>
<style global>
    	
	.d-navbar {
		background-color: white;
		transition: all 0.3s ease;
        z-index: 1;
	}

	.dark .d-navbar {
		background-color: #303030;
		color: white;
	}

	.d-navbar:not(.vertical) {
		position: absolute;
		left: 0;
		right: 0;
		top: 0;
		padding: 1rem;
		box-shadow: 0 1px 0.2rem rgba(0, 0, 0, 0.555);
	}

	.d-navbar .menu {
		flex-direction: row;
	}

	.d-navbar.vertical {
		position: absolute;
		box-shadow: 5px 0 4px -4px rgba(0, 0, 0, 0.555);
		overflow: auto;
		left: 0;
		top: 0;
		bottom: 0;
	}

	/* .sidebar-icon {
		width: 60px;
	}
	.sidebar-default {
		width: 240px;
	}
	.sidebar-compact {
		width: 120px;
	} */

	.d-navbar.fixed {
		position: fixed;
	}

	.d-navbar.vertical .menu {
		flex-direction: column;
	}

	/* @media (max-width: 700px) {
		.d-navbar.vertical:not(.open) {
			padding-left: 0;
			padding-right: 0;
			opacity: 0.5;
		}
		.d-navbar.sidebar-default {
			left: -240px;
		}
		.d-navbar.sidebar-compact {
			left: -120px;
		}
		.d-navbar.sidebar-icon {
			left: -60px;
		}

		[data-layout-sidebar] .d-page-body {
			margin-left: 0;
		}
	} */

</style>