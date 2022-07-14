<script>
    export let sidebarWidth = 0;
    export let headerHeight = 0;


    $: leftMargin = sidebarWidth > 0 ? `margin-left: ${sidebarWidth}px;` : ""
    $: topMargin = headerHeight > 0 ? `margin-top: ${headerHeight}px;` : ""
    $: style= leftMargin + topMargin

    $: console.log(style)
</script>
<div class="d-page-body" {style}>
    <slot></slot>
</div>