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
    <ul bind:offsetHeight={navBarHeight} id="navbar" in:slide out:slide>
        <li class="active">
            <a href="#">Home</a>
        </li>
        <li>
            <a href="#">Resumé</a>
        </li>
        <li>
            <a href="#">Blog</a>
        </li>
    </ul>
{/if}

<style>

    #navbar {
        list-style-type: none;
        overflow: hidden;
        padding: 0;
        margin: 0;
        width: 100%;
        background-color: orange;
        position: fixed;
    }

    #navbar > li {
        float: left;
    }

    #navbar > li > a {
        text-decoration: none;
        padding: 15px;
        text-align: center;
        display: inline-block;
        color: white;
    }

    #navbar > li:hover {
        background-color: rgba(0, 0, 0, 0.05);
    }

    .active {
        background-color: rgba(0, 0, 0, 0.3);
    }

</style>