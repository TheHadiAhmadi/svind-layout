<script>
    export let vertical  = false
    export let fixed = false;
    export let open = false;

    let className= ''
    export {className as class}; 
</script>
<nav class:open class:vertical class="{className} d-navbar" class:fixed>
    <slot/>
</nav>