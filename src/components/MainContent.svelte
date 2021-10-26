<script>
        
    export let content
        
</script>

<div class="main-content">
    {#if content.media_type === 'video'} 
        <a href={ content.url } title={ content.url } class="video-link">
            <span class="media-type">{ content.media_type }</span>
            <img src={ content.thumbnail_url } alt={ content.thumbnail_url }>
        </a>
    {:else}
        <img src={ content.url } alt={ content.url }>
    {/if}
    <div class="text-content">
        <h2 class="title">{ content.title }</h2>
        <p class="date">
            <span class="bold">Date:</span> { content.date }
        </p>
        <p class="explanation">
            { content.explanation }
        </p>
        {#if content.copyright}
            <p class="copyright">
                &copy; { content.copyright }
            </p>
        {/if}
        {#if content.hdurl}
            <a class="download-btn" href={ content.hdurl } title={ content.hdurl }>View HD</a>
        {/if}
    </div>
</div>

<style>

    .bold {
        font-weight: 800;
    }

    .video-link {
        border-radius: 0.4em;
        position: relative;
        /*width: 100%;*/
        display: block;
    }

    .video-link img {
        width: 18em;
        /*height: 100%;*/
        border-radius: 0.4em;
    }

    .main-content {
        margin-top: 2em;
        margin-bottom: 2em;
        display: flex;
        justify-content: space-between;
    }
    
    .main-content > img {
        height: 100%;
        width: 40%;
        border-radius: 0.4em;
        object-fit: cover;
        object-position: center;
    }

    .main-content .text-content {
        margin-left: 1.2em;
    }

    .main-content .text-content h2 {
        color: #FEFEFE;
        font-size: 2em;
        margin-bottom: 0.4em;
    }

    .main-content .text-content p {
        color: #FEFEFE;
        font-weight: 300;
        margin-top: 0.6em;
    }

    .main-content .text-content .download-btn {
        border-radius: 0.2em;
        font-size: 0.9em;
        margin-top: 1em;
        display: inline-block;
        color: var(--accent-color);
    }

    @media (max-width: 960px) {
        .main-content {
            margin-top: 2em;
            display: flex;
            justify-content: space-between;
        }
    }

    @media (max-width: 768px) {
        .main-content {
            margin-top: 2em;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .main-content .text-content {
            margin-left: 0;
            margin-top: 1em;
            margin-bottom: 2em;
        }

        .main-content > img {
            width: 100%;
        }

        .video-link img {
            width: 100%;
        }
    }

    .media-type {
        position: absolute;
        top: 0.4em;
        color: #FEFEFE;
        font-size: 0.8em;
        padding: 0.2em 0.8em;
        border-radius: 1000em;
        display: block;
        background-color: #DD4F43;
        right: 0.4em;
    }

</style>