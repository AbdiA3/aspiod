<script>
		
	const url = 'https://api.nasa.gov/planetary/apod?api_key=tJOWsZ9xvBHgXl4E58wve64bht5tkY0UZaO9Zgq0'

	let content = null

	let promise = fetch(url)
			     .then(res => res.json())
			     .then(data => {
			     	content = data
			     })
			     .catch(err => { alert(err) })

</script>

<div class="main">
	<header>
		<div class="brand">
			<h1>AsPiOD</h1>
			<h3>Astronomy Picture of the Day</h3>
		</div>
		<p>
			<span>Abdi Adem</span>
			<a href="https://github.com/AbdiA3/aspiod" target="_blank" title="https://github.com/AbdiA3/aspiod">
	            <svg style="width: 1.4em;" fill="#FEFEFE" role="img" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
	                <title>GitHub</title>
	                <path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/>
	            </svg>
	        </a>
		</p>
	</header>

	{#await promise}
		loading ...
	{:then data}

		<div class="main-content">
			<img src={ content.url } alt={ content.url }>

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

	{:catch error}
		{ alert(error) }
	{/await}

</div>

<style>
	.bold {
		font-weight: 800;
	} 

	.main {
		width: 70%;
		padding: 2.4em 0;
		margin: auto;
		height: 100vh;
	}

	.main header {
		color: #FEFEFE;
		display: flex;
		align-items: flex-end;
		justify-content: space-between;
		margin-bottom: 0.6em;
		padding-bottom: 0.6em;
		border-bottom: 0.1em solid #FEFEFE;
	}

	.main header h1 {
		font-size: 3.2em;
		margin-bottom: 0.1em;
	}

	.main header h3 {
		margin-bottom: 0.4em;
		font-size: 1.2em;	
		font-weight: 300;
	}

	.main header p {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.main header p * {
		/*font-size: 0.9em;*/
		font-family: 'Roboto';
		font-weight: 200;
	}

	.main header p span {
		margin-right: 1em;
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
		padding: 0.6em 2em;
		background-color: var(--accent-color);
		border-radius: 0.2em;
		text-decoration: none;
		margin-top: 1em;
		display: inline-block;
		color: #FEFEFE;
	}

	@media (max-width: 960px) {
		.main {
			/*display: none;*/
			width: 80%;
		}

		.main-content {
			margin-top: 2em;
			display: flex;
			justify-content: space-between;
		}
	}

	@media (max-width: 768px) {
		.main {
			/*display: none;*/
			width: 92%;
		}

		.main header {
			flex-direction: column;
			align-items: center;
			justify-content: center;
			text-align: center;
		}

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
	}


</style>