<script>
    
    import { createEventDispatcher } from 'svelte'


    export let content
    
    const dispatch = new createEventDispatcher()

    const open = (c) => {
        dispatch('view', c)
    }

</script>

<div class="main-wrapper">
    <div class="wrapper">
        {#each content as c (c.date)}
            <div class="image-container">
                <a href="#" on:click|preventDefault={ () => open(c) } title={ c.title }>
                    <span class="date-tag">{ c.date }</span>
                    <span class="media-type">{ c.media_type }</span>
                    {#if c.media_type ==='video'}
                        <img src={ c.thumbnail_url } alt={ c.thumbnail_url }>
                    {:else}
                        <img src={ c.url } alt={ c.url }>
                    {/if}
                </a>
            </div>
        {/each}
    </div>
</div>

<style>
    
    .wrapper {
        justify-content: center;
        display: flex;
        flex-wrap: wrap;
        gap: 1.4em;
        margin: auto;
        margin-top: 1em;
    }

    .wrapper .image-container {
        width: 12em;
        height: 14em;
        border-radius: 0.4em;
        overflow: hidden;
        position: relative;
        transition: all 0.2s ease-in-out;
    }

    .wrapper .image-container:hover {
        transform: scale(1.02);
    }

    .wrapper .image-container .date-tag,
    .wrapper .image-container .media-type {
        position: absolute;
        top: 0.4em;
        background-color: var(--accent-color);
        color: #FEFEFE;
        font-size: 0.8em;
        padding: 0.2em 0.8em;
        border-radius: 1000em;
        display: block;
    }
    .wrapper .image-container .date-tag {
        left: 0.4em;
    }

    .wrapper .image-container .media-type {
        background-color: #DD4F43;
        right: 0.4em;

    }

    .wrapper .image-container img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

</style>