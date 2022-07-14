<script>
    export let vertical  = false
    export let fixed = false;
    export let open = false;
    
    export let width = 0;
    export let height = 0;

    export let top = 0

    let className= ''
    export {className as class}; 

    $: styleTop =  top > 0 ? `top: ${top}px;` : ''
    $: styleWidth =  width > 0 ? `width: ${width}px;` : ''
    $: styleHeight = height > 0 ? `height: ${height}px;` : ''
    $: style = styleTop + styleWidth + styleHeight
</script>
<nav {style} class:open class:vertical class="{className} d-navbar" class:fixed>
    <slot/>
</nav>