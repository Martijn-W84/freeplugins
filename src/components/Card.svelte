<script>
    export let plugin;
    export let show;
</script>

{#if show}
<li class="link-card">
	<a href={plugin.url} target="_blank" rel="noreferrer">
		<img src={plugin.img} alt={plugin.name} width={plugin.imgwidth}/>
		<div class="title-container">
			<h2>{plugin.name}</h2>
			<div class="category">{plugin.category}</div>
		</div>
		<h3>{plugin.developer}</h3>
		<p>
			{plugin.descr}
		</p>
	</a>
</li>
{/if}

<style>
	.title-container {
		display:flex;
		justify-content: space-between;
		margin-top: 16px;
		margin-bottom: 16px;
	}

	.link-card {
		list-style: none;
		display: flex;
		padding: 0.15rem;
		background-color: white;
		background-size: 400%;
		border-radius: 0.5rem;
		background-position: 100%;		
		box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.1);
		transition: 200ms;
    	transition-timing-function: ease-in-out;
	}

	.link-card > a {
		width: 100%;
		text-decoration: none;
		line-height: 1.4;
		padding: 1rem 1.3rem;
		border-radius: 0.35rem;
		color: #111;
		background-color: white;		
	}
	h2 {
		margin: 0;
		font-size: 1.25rem;
		transition: color 0.6s cubic-bezier(0.22, 1, 0.36, 1);
		line-height: 1.75rem;
	}
	h3 {
		margin: 0;
		font-size: 1rem;
		transition: color 0.6s cubic-bezier(0.22, 1, 0.36, 1);
		line-height: 1.4rem;
	}
	img{
		width: 100%;
        border-radius: 10px;
		min-height: 50px;
	}
	p {
		margin-top: 0.5rem;
		margin-bottom: 0;
		color: #000;
		line-height: 1.4rem;
	}
	.link-card:is(:hover, :focus-within) {
		background-position: 0;
		transform: scale(1.02);
		box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
	}
</style>
