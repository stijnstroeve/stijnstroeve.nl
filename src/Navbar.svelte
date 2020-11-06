<script>
    import { onMount } from 'svelte';
    import { slide } from 'svelte/transition';
    import Earth from './Earth.svelte';

    let yPos = 0;
    let navBarHeight = 0;
    let visible = false;

    onMount(() => {
        visible = true;
    })

    $: {
        // If the yPos is higher than the navbar height, we should hide the navbar.
        // visible = yPos <= navBarHeight;
    }
</script>

<svelte:window bind:scrollY={yPos} />

{#if visible}
<!--    <ul bind:offsetHeight={navBarHeight} id="navbar" in:slide out:slide>-->
<!--        <Earth />-->

<!--        <li class="active">-->
<!--            <a href="#">Home</a>-->
<!--        </li>-->
<!--        <li>-->
<!--            <a href="#">Resumé</a>-->
<!--        </li>-->
<!--        <li>-->
<!--            <a href="#">Blog</a>-->
<!--        </li>-->
<!--    </ul>-->

    <div>

<!--        <ul>-->
<!--            <li>-->
<!--                <a href="#">About</a>-->
<!--            </li>-->
<!--            <li>-->
<!--                <a href="#">Timeline</a>-->
<!--            </li>-->
<!--        </ul>-->

        <Earth />

<!--        <ul>-->
<!--            <li>-->
<!--                <a href="#">Projects</a>-->
<!--            </li>-->
<!--            <li>-->
<!--                <a href="#">Resumé</a>-->
<!--            </li>-->
<!--        </ul>-->

    </div>


{/if}

<style>

    div {
        display: flex;
        justify-content: space-evenly;
        /*justify-content: space-between;*/
        /*gap: 500px;*/
    }

    ul {
        list-style-type: none;
        overflow: hidden;

    }

    ul > li {
        float: left;
        padding: 20px;
    }

    ul > li > a {
        font-family: dtm-mono;
        font-size: 32px;
        text-transform: uppercase;
        text-decoration: none;
        color: white;
        text-shadow: 2px 2px rgb(100,100,100);
    }

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