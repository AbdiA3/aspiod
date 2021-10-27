<script>

    import { createEventDispatcher } from 'svelte'
    import Overlay from './Overlay.svelte'    

    const dispatch = new createEventDispatcher()

    let date_type = true
    let date
    let start_date
    let end_date

    const min_date = new Date('1995-06-16')
    const today = new Date()
    let invalid_date_min
    let invalid_date_max
    let valid = true

    const close = () => {
        dispatch('close')
    }

    const date_selected = () => {
        let date_object = new Date(date)
        let start_date_object = new Date(start_date)
        let end_date_object = new Date(end_date)
        if((date_object < min_date  || start_date_object < min_date) && (date_object > today || end_date_object > today)) {
            invalid_date_min = 'The date you select must be after 1995-06-16'
            invalid_date_max = 'The date you select must not be after today'
        } else if(date_object < min_date  || start_date_object < min_date) {
            invalid_date_min = 'The date you select must be after 1995-06-16'
            invalid_date_max = null
        } else if(date_object > today || end_date_object > today) {
            invalid_date_max = 'The date you select must not be after today'
            invalid_date_min = null
        } else {
            invalid_date_max = null
            invalid_date_min = null
            dispatch('date_selected', { date, start_date, end_date })
        }

    }

    const change_date_type = () => {
        date_type = !date_type

        if(date_type) {
            start_date = ''
            end_date = ''
        } else {
            date = ''
        }
        
        invalid_date_max = null
        invalid_date_min = null
    }

</script>

<Overlay on:close={ close }>

    <div class="date-selector-card">
        <button class="toggle" type="button" on:click={ change_date_type }>
            Change to 
            {#if date_type}
                date range
            {:else}
                single date
            {/if}
        </button>
        {#if date_type}
            <div class="single-date">
                <div class="input-field">
                    <label for="date">Select a date</label>
                    <input bind:value={ date } id="date" type="date" name="date">
                    {#if invalid_date_min}
                        <p class="error">{ invalid_date_min }</p>
                    {/if}
                    {#if invalid_date_max}
                        <p class="error">{ invalid_date_max }</p>
                    {/if}
                </div>
            </div>
        {:else}
            <div class="date-range">
                <div class="input-field">
                    <label for="start-date">Start Date</label>
                    <input bind:value={ start_date } type="date" name="start_date" id="start-date">
                    {#if invalid_date_min}
                        <p class="error">{ invalid_date_min }</p>
                    {/if}
                </div>

                <div class="input-field">
                    <label for="end-date">End Date</label>
                    <input bind:value={ end_date } type="date" name="end_date" id="end-date">
                    {#if invalid_date_max}
                        <p class="error">{ invalid_date_max }</p>
                    {/if}
                </div>
            </div>
        {/if}
        <button class="done" type="button" on:click|self={ date_selected }>
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