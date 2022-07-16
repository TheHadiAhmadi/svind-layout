<div class="d-page-body">
    <slot></slot>
</div>

<style global>

	.d-page-body {
        margin-left: var(--sidebar-width);
        margin-top: var(--header-height);
        margin-bottom: var(--footer-height);
		padding: 1rem;
        position: relative;
        overflow: auto;
		transition: all 0.3s ease;
	}

    .dark .d-page-body {
		background-color: #202020;
		color: white;
	}
</style>