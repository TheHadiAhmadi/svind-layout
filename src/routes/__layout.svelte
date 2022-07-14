<script lang="ts">
	import { Button, Card, CardBody, Checkbox, FormGroup, Icon, Label, Menu, MenuItem } from '@svind/svelte';
	import { Page, Navbar, PageBody } from '$lib/components';
	import '@svind/svelte/styles.css';
	import Header from '$lib/components/Header.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
import Drawer from '$lib/components/Drawer.svelte';

import {sidebarWidth, headerHeight} from '$lib/stores'
import { writable } from 'svelte/store';

	let drawerWidth = writable(240);

	let drawerOpen = false;

	let dark = false;
	let fixed = false;

	let hasSidebar = true;
	let hasHeader = true;

	$: sidebarMode = $sidebarWidth < 120 ? 'icon' : $sidebarWidth < 200 ? 'compact' : 'default' 

</script>

<Page {dark} {fixed}>
	<Drawer width={$drawerWidth} open={drawerOpen}>
		<div class="flex justify-end">

			<Button circle on:click={() => drawerOpen = false}>
				<Icon icon="la:times"/>
			</Button>
		</div>
		<br/>
		<div class="p-2">
			<Checkbox bind:value={fixed}>fixed</Checkbox>
			<Checkbox bind:value={dark}>dark</Checkbox>
			<br>
			<br>
			<Checkbox bind:value={hasHeader}>hasHeader</Checkbox>
			<Checkbox bind:value={hasSidebar}>hasSidebar</Checkbox>
			<br>
			<br>

			<FormGroup>
				<Label for="">Sidebar Mode</Label>

				<select bind:value={sidebarMode} class="form-control">
					<option>default</option>
					<option>compact</option>
					<option>icon</option>
				</select>
			</FormGroup>

			<label>
				Sidebar: <input type="range" max="1000" bind:value={$sidebarWidth}>
			</label>
			<label>
				Drawer: <input disabled type="range" max="1000" bind:value={$drawerWidth}>
			</label>
			<label>
				Header: <input type="range" max="400" bind:value={$headerHeight}>
			</label>

		</div>
	</Drawer>
	{#if hasHeader}
		<Header height={$headerHeight} class="flex items-center justify-between">
			<Menu>
				<MenuItem>item</MenuItem>
				<MenuItem>item</MenuItem>
			</Menu>
			<div>
				<Button square on:click={() => drawerOpen = !drawerOpen}>
					<Icon icon="la:bars"/>
				</Button>
			</div>
		</Header>
	{/if}
	{#if hasSidebar}
		<Sidebar top={$headerHeight} width={$sidebarWidth} mode={sidebarMode}>
			<Menu>
				<MenuItem class="flex items-center {sidebarMode !== 'default' ? 'justify-center' : ''}">
					<Icon icon="la:plane" />
					<span class:hidden={sidebarMode === 'icon'}>Flight</span>
				</MenuItem>
				<MenuItem class="flex items-center {sidebarMode !== 'default' ? 'justify-center' : ''}">
					<Icon icon="la:box" />
					<span class:hidden={sidebarMode === 'icon'}>Packages</span>
				</MenuItem>
			</Menu>
		</Sidebar>
	{/if}

	<PageBody sidebarWidth={$sidebarWidth} headerHeight={$headerHeight}>
		<Card z="2">
			<CardBody>
				<label>
					Drawer: <input type="range" max="1000" bind:value={$drawerWidth}>
				</label>
				<Button on:click={() => drawerOpen = !drawerOpen}>
					<Icon icon="la:bars"/> Open Drawer
				</Button>
				<br>
				<slot />
			</CardBody>
		</Card>
	</PageBody>
</Page>

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
		z-index: 1;
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
	.d-page {
		position: relative;
		overflow: hidden;
		width: 100%;
		min-height: 100vh;
		background-color: #efefef;
	}

	.dark .d-page-body {
		background-color: #202020;
		color: white;
	}

	.d-page-body {
		padding: 1rem;
		transition: all 0.3s ease;
	}

	/* [data-layout-sidebar='icon'] .d-page-body {
		margin-left: 60px;
	}
	[data-layout-sidebar='compact'] .d-page-body {
		margin-left: 120px;
	}
	[data-layout-sidebar='default'] .d-page-body {
		margin-left: 240px;
	} */

	[data-layout-header] .d-page-body {
		transition: all 0.3s ease;
	}

	.d-navbar {
		background-color: white;
		transition: all 0.3s ease;
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
		/* height: 80px; */
		box-shadow: 0 1px 0.2rem rgba(0, 0, 0, 0.555);
	}

	.d-navbar .menu {
		flex-direction: row;
	}

	/* [data-layout-header] .d-navbar.vertical {
		top: 80px;
	} */

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

	@media (max-width: 700px) {
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
	}
</style>
