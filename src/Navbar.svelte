<script>
    import { onMount } from 'svelte';
    import { slide } from 'svelte/transition';

    let yPos = 0;
    let navBarHeight = 0;
    let visible = false;

    onMount(() => {
        visible = true;
    })

    $: {
        // If the yPos is higher than the navbar height, we should hide the navbar.
        visible = yPos <= navBarHeight;
    }
</script>

<svelte:window bind:scrollY={yPos} />

{#if visible}
    <div bind:offsetHeight={navBarHeight} id="navbar" in:slide out:slide>
        <li>
            <a href="#">Home</a>
            <a href="#">Resumé</a>
            <a href="#">Blog</a>
        </li>
    </div>
{/if}

<style>

    #navbar {
        width: 100%;
        height: 50px;
        background-color: orange;
        position: fixed;
    }

</style>