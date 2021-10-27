<script>

    import { createEventDispatcher } from 'svelte'
    

    const dispatch = new createEventDispatcher()

    const close = () => {
        dispatch('close')
    }

    const close_key = (evt) => {
        if(evt.key === 'Escape') close()
    }

</script>

<svelte:window on:keydown = { close_key } />
<div class="overlay" on:click|self={ close }>
    <slot></slot>
</div>

<style>
    
    .overlay {
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.6);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 10000;
    }

</style>