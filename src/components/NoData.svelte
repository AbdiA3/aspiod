<script>
        
    import Overlay from './Overlay.svelte'

</script>


<Overlay on:close>
    
    <div class="card">        
        <h1>There is no data for this day.</h1>
    </div>

</Overlay>

<style>
    
    .card {
        background-color: #FEFEFE;
        /*width: 10em;*/
        /*height: 10em;/*/
        padding: 3em;
        border-radius: 0.4em;
        text-align: center;
    }

    .card h1 {
        font-size: 1.8em;
        font-weight: 300;
    }



</style>