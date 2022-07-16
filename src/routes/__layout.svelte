<script lang="ts">
	import { Button, Card, CardBody, Checkbox, FormGroup, Icon, Label, Menu, MenuItem } from '@svind/svelte';
	import { Page, Navbar, PageBody } from '$lib/components';
	import '@svind/svelte/styles.css';
	import Header from '$lib/components/Header.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
import Drawer from '$lib/components/Drawer.svelte';

// import {sidebarWidth, headerHeight} from '$lib/stores'
import { writable } from 'svelte/store';
import Footer from '$lib/components/Footer.svelte';

	let drawerWidth = writable(240);

	let drawerOpen = false;

	let dark = false;
	let fixed = false;

	let hasSidebar = true;
	let hasHeader = true;

	let footerFullWidth = false
	let headerFullWidth = false

	let sidebarWidth = 240;
	let headerHeight = 64;
	let footerHeight = 64;

	$: sidebarMode = sidebarWidth < 120 ? 'icon' : sidebarWidth < 200 ? 'compact' : 'default' 

</script>
<!-- <slot/> -->


<Page {dark}>
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
				Sidebar: <input type="range" max="1000" bind:value={sidebarWidth}>
			</label>
			<label>
				Drawer: <input disabled type="range" max="1000" bind:value={$drawerWidth}>
			</label>
			<label>
				Header: <input type="range" max="400" bind:value={headerHeight}>
			</label>
			<label>
				Header Full: <input type="checkbox" bind:checked={headerFullWidth}>
			</label>
			<label>
				Footer: <input type="range" max="400" bind:value={footerHeight}>
			</label>
			<label>
				Footer Full: <input type="checkbox" bind:checked={footerFullWidth}>
			</label>

		</div>
	</Drawer>
	{#if hasHeader}
		<Header fullWidth={headerFullWidth} {fixed} bind:height={headerHeight} class="flex items-center justify-between">
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
		<Sidebar fullWidth={footerFullWidth} {fixed} dark bind:width={sidebarWidth} mode={sidebarMode}>
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

	<PageBody>
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

	<Footer height={footerHeight} fullWidth={footerFullWidth}>
		this is footer
	</Footer>
</Page>
