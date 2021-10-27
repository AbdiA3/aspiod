<script>

    import { createEventDispatcher } from 'svelte'
    

    const dispatch = new createEventDispatcher()
    
    const close_date_selector = () => {
        dispatch('close_date_selector')
    }

    const close_date_selector_key = (evt) => {
        if(evt.key === 'Escape') close_date_selector()
    }

</script>

<svelte:window on:keydown = { close_date_selector_key } />
<div class="overlay" on:click|self={ close_date_selector }>
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