<script>
    import SmallArrow from './SmallArrow.svelte';
    import { fly } from 'svelte/transition';
    import { onMount } from 'svelte';

    onMount(() => {
        startAutoTransition();
    })

    let currentWordIndex = 0;
    const words = [
        {
            word: 'Programmer',
            color: '#E8A60C'
        },
        {
            word: 'Perfectionist',
            color: '#db3b3b'
        },
        {
            word: 'Man',
            color: 'green'
        }
    ];

    // The transition time between the shown texts.
    const transitionTime = 250;
    let isTransitioning = false;

    const autoTransitionDelay = 5000;
    let autoTranslateInterval;

    /**
     * Starts the auto transition.
     * If the interval is already started, the interval will be restarted.
     */
    function startAutoTransition() {
        if(autoTranslateInterval != null) {
            clearInterval(autoTranslateInterval);
        }

        autoTranslateInterval = setInterval(() => {
            setIndex(currentWordIndex + 1);
        }, autoTransitionDelay);
    }

    function setIndex(nextIndex) {
        if(currentWordIndex === nextIndex) return;

        // If there is a transition occuring, we don't want to be able to update the index.
        if(isTransitioning) return;

        if(nextIndex > words.length - 1) {
            nextIndex = 0;
        } else if(nextIndex < 0) {
            nextIndex = words.length - 1;
        }

        // Restart the auto transition so there will be no chance for double transitions.
        startAutoTransition();

        isTransitioning = true;
        setTimeout(() => {
            currentWordIndex = nextIndex;
            isTransitioning = false;
        }, transitionTime);
    }
</script>

<h2>Hey there, I'm a</h2>
<div class="hero-text">
    <SmallArrow buttonClicked={() => setIndex(currentWordIndex-1)} flipped={false} />

    {#each words as { word, color }, i}
        {#if currentWordIndex === i && !isTransitioning}
            <h1 transition:fly="{{ y: 100, duration: transitionTime }}" style="color: {color};">
                {word}
            </h1>
        {/if}
    {/each}

    <SmallArrow buttonClicked={() => setIndex(currentWordIndex+1)} flipped={true} />
</div>

<div class="dots">
    {#each words as word, i}
        <div on:click={() => setIndex(i)} class:active={i === currentWordIndex} class="dot"></div>
    {/each}
</div>

<style>
    .dots {
        display: flex;
        justify-content: center;
        margin-top: -20px;
    }

    .dot {
        width: 10px;
        background-color: #707070;
        height: 10px;
        border-radius: 5px;
        margin: 5px;
    }

    .active {
        background-color: rgba(255, 255, 255, 0.55);
    }

    h1, h2 {
        font-family: 'Poppins', sans-serif;
    }

    h1 {
        font-size: 125px;
        margin: 0;
        user-select: none;
        width: 1000px;
    }

    h2 {
        font-size: 50px;
        color: #FFFFFF;
        margin-bottom: 0;
        user-select: none;
    }

    .hero-text {
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>