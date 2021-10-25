<script>

    import { createEventDispatcher } from 'svelte'
    

    const dispatch = new createEventDispatcher()

    let date_type = 1
    let date
    let start_date
    let end_date

    const close_date_selector = () => {
        dispatch('close_date_selector')
    }

    const close_date_selector_key = (evt) => {
        if(evt.key === 'Escape') close_date_selector() 
    }

</script>


<div class="overlay" on:click|self={ close_date_selector } on:keydown = { close_date_selector_key }>
    <div class="date-selector-card">
        <button class="toggle" type="button" on:click={ () => { date_type = !date_type } }>
            Change to 
            {#if date_type == 1}
                date range
            {:else}
                single date
            {/if}
        </button>
        {#if date_type == 1}
            <div class="single-date">
                <div class="input-field">
                    <label for="date">Select a date</label>
                    <input id="date" type="date" name="date">
                </div>
            </div>
        {:else}
            <div class="date-range">
                <div class="input-field">
                    <label for="start-date">Start Date</label>
                    <input type="date" name="start_date" id="start-date">
                </div>

                <div class="input-field">
                    <label for="end-date">End Date</label>
                    <input type="date" name="end_date" id="end-date">
                </div>
            </div>
        {/if}
        <button class="done" type="button">
            Done
        </button>
    </div>
</div>

<style>
    .overlay {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0, 0, 0, 0.6);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .date-selector-card {
        background-color: #FEFEFE;
        /*width: 10em;*/
        /*height: 10em;/*/
        padding: 1.4em 3em;
        border-radius: 0.4em;

    }

    .date-selector-card button.toggle {
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

    .date-selector-card button.done {
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
    
    .date-selector-card .input-field {
        margin-bottom: 1.2em;
    }
    
    .date-selector-card .input-field label {
        margin-bottom: 0.4em;
        font-weight: 700;
    }

    .date-selector-card .input-field input {
        width: 18em;
        height: 2.4em;
        padding: 0.4em;
    }

    .date-selector-card .input-field * {
        display: block;
    }

</style>