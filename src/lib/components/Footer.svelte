<script>
import { getContext, onDestroy, onMount } from "svelte";


    export let fixed = false
    export let height= 0;
    export let fullWidth = false

    const { footerHeight, hasFooter} = getContext('layout')


    onMount(()=> {
        $hasFooter = true  
    })


    onDestroy(() => {
        $hasFooter = false
    })

    $: $footerHeight = height;
    $: $hasFooter = fullWidth ? 'full' : true
    
</script>
<footer class:fixed class:full={fullWidth} class="d-footer">
    <slot/>
</footer>

<style global>

    .d-footer.fixed {
        position: fixed;
        bottom: 0;
        width: 100%;
    }

    .d-footer {
        height: var(--footer-height);
        padding: 1rem;
        position: absolute;
        background-color: #cdcdcd;
        bottom: 0;
        right: 0;
        left: var(--sidebar-width);
        z-index: 2;
    }
    .d-footer.full {
        left: 0;
    }

    .dark .d-footer {
        background-color: #404040;
        color: white;
    }

    .d-page-body .d-footer {
        margin-left: -1rem;
        margin-right: -1rem;
        margin-bottom: -1rem;
    }

    .d-page-body .d-footer.fixed {
        margin-bottom: 0;
        /* left: var(--sidebar-width); */
    }
</style>