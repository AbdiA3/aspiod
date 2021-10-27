<script>
        
    import Overlay from './Overlay.svelte'
    import { createEventDispatcher } from 'svelte'


    const dispatch = new createEventDispatcher()

    let count = 10

    const close = () => {
        dispatch('close')
    }

    const count_input = () => {
        dispatch('set_count', count)
    }

    const check_keypress = (evt) => {
        if(evt.key === 'Enter') count_input()
    }


</script>

<svelte:window on:keydown={ check_keypress } />
<Overlay on:close={ close }>

    <div class="card">
        <div class="input-field">
            <label for="count">How many images do you want?</label>
            <input autofocus bind:value={ count } id="count" type="number" name="count">
        </div>

        <button class="done" type="button" on:click|self={ count_input }>
            Done
        </button>
    </div>

</Overlay>

<style>

    .error {
        font-size: 0.8em;
        margin-top: 0.3em;
        color: orangered;
    }

    .card {
        background-color: #FEFEFE;
        /*width: 10em;*/
        /*height: 10em;/*/
        padding: 1.4em 3em;
        border-radius: 0.4em;

    }

    .card button.toggle {
        margin-bottom: 1em;
        padding: 0.6em 2em;
        background-color: var(--bg-color);
        border-radius: 0.2em;
        text-decoration: none;
        display: inline-block;
        color: #FEFEFE;
        border: none;
        cursor: pointer;
    }

    .card button.done {
        /*margin-bottom: 1em;*/
        padding: 0.6em 2em;
        background-color: var(--accent-color);
        border-radius: 0.2em;
        text-decoration: none;
        display: inline-block;
        color: #FEFEFE;
        border: none;
        cursor: pointer;
        width: 100%;
        text-align: center;
    }
    
    .card .input-field {
        margin-bottom: 1.2em;
    }
    
    .card .input-field label {
        margin-bottom: 0.4em;
        font-weight: 700;
    }

    .card .input-field input {
        width: 18em;
        height: 2.4em;
        padding: 0.4em;
    }

    .card .input-field * {
        display: block;
    }
    
</style>