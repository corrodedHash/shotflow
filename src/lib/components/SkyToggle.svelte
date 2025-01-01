<script>
    let { checked = $bindable(false), labelOn = "", labelOff ="" } = $props();
</script>

<div
    onclick={() => {
        checked = !checked;
    }}
>
    {checked ? "-" : ""}
    {checked ? labelOn : labelOff}
    {!checked ? "-" : ""}
</div>
