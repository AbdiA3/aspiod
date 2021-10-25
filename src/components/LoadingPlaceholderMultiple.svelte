<script></script>

<div class="wrapper">
    <div class="placeholder"></div>
    <div class="placeholder"></div>
    <div class="placeholder"></div>
    <div class="placeholder"></div>
    <div class="placeholder"></div>
    <div class="placeholder"></div>
    <div class="placeholder"></div>
    <div class="placeholder"></div>
    <div class="placeholder"></div>
    <div class="placeholder"></div>
</div>

<style>
    .wrapper {
        justify-content: center;
        display: flex;
        flex-wrap: wrap;
        gap: 2em;
        margin-top: 1em;
    }

    .wrapper .placeholder {
        width: 12em;
        height: 14em;
        background-color: rgba(200, 200, 200, 0.3);
        border-radius: 0.4em;
        object-fit: cover;
        object-position: center;
        animation: 1s infinite blink;
    }

    @keyframes blink {
        0% {
           background-color: rgba(200, 200, 200, 0.3); 
        }

        50% {
            background-color: rgba(200, 200, 200, 0.1);
        }

        100% {
            background-color: rgba(200, 200, 200, 0.3);
        }
    }
    
</style>