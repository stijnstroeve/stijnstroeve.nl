<script>
    import Navbar from "./Navbar.svelte";
    import HeroText from './HeroText.svelte';

    export let name;
</script>

<main>
    <div id="front-panel">
        <div class="container">
            <Navbar />
            <HeroText />
        </div>

    </div>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
</main>

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

<style>

    #front-panel {
        width: 100%;
        height: 100vh;
        background: radial-gradient(circle, rgba(20,25,42,1) 0%, rgba(17,21,35,1) 63%, rgba(11,14,24,1) 100%);
    }

    .container {
        width: 80%;
        margin: 0 auto;
    }

	main {
		text-align: center;
        max-width: 120rem;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>