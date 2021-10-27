<script>

	import MainContent from './components/MainContent.svelte'
	import Header from './components/Header.svelte'
	import MainContentMultiple from './components/MainContentMultiple.svelte'
	import LoadingPlaceholder from './components/LoadingPlaceholder.svelte'
	import LoadingPlaceholderMultiple from './components/LoadingPlaceholderMultiple.svelte'
	import DateSelector from './components/DateSelector.svelte'
	import TextInput from './components/TextInput.svelte'
	import NoData from './components/NoData.svelte'
		

	const base_url = 'https://api.nasa.gov/planetary/apod?api_key=tJOWsZ9xvBHgXl4E58wve64bht5tkY0UZaO9Zgq0&thumbs=true'

	let url = base_url
	let multiple = false

	let content = {}

	let date_selector = false
	let count_input = false

    const set_date = (evt) => {
    	date_selector = false
    	let date = evt.detail.date ?? ''
    	let start_date = evt.detail.start_date ?? ''
    	let end_date = evt.detail.end_date ?? ''

    	if(date) {
    		url = `${base_url}&date=${date}`
    		multiple = false
    	} else {
    		url = `${base_url}&start_date=${start_date}&end_date=${end_date}`
    		multiple = true
    	}
    }

    const get_n_random = (evt) => {
    	count_input = false
    	const n = evt.detail
    	url = `${base_url}&count=${n}`
    	promise = fetch(url)
			     .then(res => res.json())
			     .then(data => {
			     	content = data
			     })
			     .catch(err => { alert(err) })
    	multiple = true
    }

    const view = (evt) => {
    	content = evt.detail
    	multiple = false
    }

    const return_home = () => {
    	url = base_url
    }

	$: promise = fetch(url)
			     .then(res => res.json())
			     .then(data => {
			     	content = data
			     })
			     .catch(err => { alert(err) })

</script>

<div class="main">
	
	{#if date_selector}
		<DateSelector on:close={ () => { date_selector = false } } on:date_selected={ set_date } />
	{/if}

	{#if count_input}
		<TextInput on:close={ () => { count_input = false } } on:set_count={ get_n_random } />
	{/if}

	<Header on:open_date_selector={ () => { date_selector = !date_selector } } on:open_random_image={ () => { count_input = !count_input } } />

	{#if !multiple}
		{#await promise}
			<LoadingPlaceholder />
		{:then data}
			{#if content.code && content.code == 404}
				<NoData on:close={ return_home } />
			{:else}
				<MainContent { content } />
			{/if}
		{:catch error}
			{ alert(error) }
		{/await}
	{:else}
		{#await promise}	
			<LoadingPlaceholderMultiple />
		{:then data}
			<MainContentMultiple { content } on:view={ view } />
		{:catch error}
			{ alert(error) }
		{/await}
	{/if}

</div>

<style>

	.main {
		width: 70%;
		padding: 2.4em 0;
		margin: auto;
		min-height: 100vh;
	}

	@media (max-width: 960px) {
		.main {
			/*display: none;*/
			width: 80%;
		}
	}

	@media (max-width: 768px) {
		.main {
			/*display: none;*/
			width: 92%;
		}
	}

</style>