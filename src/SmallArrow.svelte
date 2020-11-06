<script>
    export let flipped;
    export let buttonClicked;
</script>

<svg on:click={buttonClicked} class="{flipped ? 'flipped' : ''}" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="32.07" height="52.313" viewBox="0 0 32.07 52.313">
    <defs>
        <filter id="Arrow_left" x="0" y="0" width="32.07" height="52.313" filterUnits="userSpaceOnUse">
            <feOffset dy="3" input="SourceAlpha"/>
            <feGaussianBlur stdDeviation="1.5" result="blur"/>
            <feFlood flood-opacity="0.161"/>
            <feComposite operator="in" in2="blur"/>
            <feComposite in="SourceGraphic"/>
        </filter>
    </defs>

    <g transform="matrix(1, 0, 0, 1, 0, 0)" filter="url(#Arrow_left)">
        <path id="Arrow_left-2" data-name="Arrow left" d="M4543.307,511.6l-20.949,20.949,20.949,20.949" transform="translate(-4516.44 -509.39) " fill="none" stroke="rgba(177,177,177,0.19)" stroke-width="2"/>
    </g>
</svg>

<style>

    .flipped {
        transform: rotate(180deg);
    }
</style>