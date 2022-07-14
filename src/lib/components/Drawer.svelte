<script>
    export let open = false;
    export let width = 200;
</script>
<div style="width: {width }px; right: -{width}px" class="d-drawer" class:open>
    <slot/>
</div>