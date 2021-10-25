<script>
        
</script>

<div class="main-content">
    <div class="img"></div>

    <div class="text-content">
        <h2 class="title"></h2>
        <p class="date"></p>
        <p class="explanation"></p>
        <p class="copyright"></p>
        <div class="download-btn"></div>
    </div>
</div>

<style>

    .bold {
        font-weight: 800;
    }

    .main-content {
        margin-top: 2em;
        margin-bottom: 2em;
        display: flex;
        justify-content: space-between;
    }
    
    .main-content .img {
        width: 40%;
        height: 18em;
        background-color: rgba(200, 200, 200, 0.3);
        border-radius: 0.4em;
        object-fit: cover;
        object-position: center;
        animation: 1s infinite blink;
    }

    .main-content .text-content {
        margin-left: 1.2em;
        width: 55%;
        border-radius: 0.4em;
    }

    .main-content .text-content h2 {
        animation: 1s infinite blink;
        background-color: rgba(200, 200, 200, 0.3);
        width: 100%;
        height: 2em;
        margin-bottom: 0.4em;
        border-radius: 0.4em;
    }

    .main-content .text-content p.date {
        animation: 1s infinite blink;
        background-color: rgba(200, 200, 200, 0.3);
        width: 8em;
        height: 1.4em;
        margin-top: 0.6em;
        border-radius: 0.4em;
    }

    .main-content .text-content p.explanation {
        animation: 1s infinite blink;
        background-color: rgba(200, 200, 200, 0.3);
        width: 100%;
        height: 14em;
        margin-top: 0.6em;
        border-radius: 0.4em;
    }

    .main-content .text-content p.copyright {
        background-color: rgba(200, 200, 200, 0.3);
        animation: 1s infinite blink;
        width: 12em;
        height: 1.4em;
        margin-top: 0.6em;
        border-radius: 0.4em;
    }

    .main-content .text-content .download-btn {
        animation: 1s infinite blink;
        width: 9em;
        height: 3em;
        background-color: rgba(200, 200, 200, 0.3);
        border-radius: 0.4em;
        margin-top: 1em;
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
            width: 100%;
        }

        .main-content .img {
            width: 100%;
        }
    }

    @keyframes blink {
        0% {
           background-color: rgba(200, 200, 200, 0.3); 
        }

        50% {
            background-color: rgba(0, 0, 0, 0.2);
        }

        100% {
            background-color: rgba(200, 200, 200, 0.3);
        }
    }

</style>