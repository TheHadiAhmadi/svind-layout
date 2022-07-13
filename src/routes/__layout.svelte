<script lang="ts">
    import {Card, CardBody, Checkbox, FormGroup, Icon, Label, Menu, MenuItem} from '@svind/svelte'
    import {Page, Navbar, PageBody} from '$lib/components'
    import '@svind/svelte/styles.css'
import Header from '$lib/components/Header.svelte';
import Sidebar from '$lib/components/Sidebar.svelte';

let sidebarMode = 'default';

let dark = false;
let fixed = false;

</script>
<Page {dark} {fixed}>
    <Header>
        <Menu>
            <MenuItem>item</MenuItem>
            <MenuItem>item</MenuItem>
        </Menu>
    
    </Header>
    <Sidebar mode={sidebarMode}>
        <Menu>
            <MenuItem class="flex items-center {sidebarMode !== 'default' ? 'justify-center' : ''}">
                <Icon icon="la:plane"/>
                <span class:hidden={sidebarMode === 'icon'}>Flight</span>
            </MenuItem>
            <MenuItem class="flex items-center {sidebarMode !== 'default' ? 'justify-center' : ''}">
                <Icon icon="la:box"/>
                <span class:hidden={sidebarMode === 'icon'}>Packages</span>
            </MenuItem>
        </Menu>
    </Sidebar>

    <PageBody>
        <Card z=2>
            <CardBody>

                <Checkbox bind:value={fixed}>
                    fixed
                </Checkbox>
                <Checkbox bind:value={dark}>
                    dark
                </Checkbox>

                <FormGroup>
                    <Label for="">Sidebar Mode</Label>

                    <select bind:value={sidebarMode} class="form-control">
                        <option>default</option>
                        <option>compact</option>
                        <option>icon</option>
                        
                    </select>
                </FormGroup>

                <slot/>
            </CardBody>
        </Card>
    
    </PageBody>
</Page>

<style global>
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

    [data-layout-sidebar="icon"] .d-page-body {
        margin-left: 60px;
    }
    [data-layout-sidebar="compact"] .d-page-body {
        margin-left: 120px;
    }
    [data-layout-sidebar="default"] .d-page-body {
        margin-left: 240px;
    }

    [data-layout-header] .d-page-body {
        margin-top: 80px;
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
        height: 80px;
        box-shadow: 0 1px 0.2rem rgba(0, 0, 0, 0.555); 

    }

    .d-navbar .menu {
        flex-direction: row;
    }

    [data-layout-header] .d-navbar.vertical {
        top: 80px;
        bottom: 0;
    }

    .d-navbar.vertical {
        position: absolute;
        box-shadow: 5px 0 4px -4px rgba(0, 0, 0, 0.555); 
        overflow: auto; 
        left: 0;
    }

    .sidebar-icon {
        width: 60px;
    }
    .sidebar-default {
        width: 240px;
    }
    .sidebar-compact {
        width: 120px;
    }


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

