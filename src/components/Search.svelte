<script lang="ts">
	$: searchActive = searchTerm != "";
	export let searchTerm: string;
	export let elm;	
</script>

<div id="search-input-cont">
	<input type="text" 
				id="search-field" 
				placeholder="" 
				autocomplete="off"
				bind:value={searchTerm}
				on:input
				bind:this={elm} />
	 <svg width="32" height="32" viewBox="0 0 322 322" fill="none" xmlns="http://www.w3.org/2000/svg" class:searchActive on:click on:keyup>
		<circle id="circle" cx="139" cy="131" r="90" stroke="black" stroke-width="25" class:searchActive/>
		<line id="posLine" x1="209.142" y1="204" x2="282.681" y2="277.539" stroke="black" stroke-width="25" stroke-linecap="round" class:searchActive/>
		<line id="negLine" x1="209.142" y1="204" x2="282.681" y2="277.539" stroke="black" stroke-width="25" stroke-linecap="round" class:searchActive/>					
	</svg>	
</div>

<style>
	#search-input-cont {
		width: 50%;
		display: flex;
		align-items: center;
		margin: 0 0 0px 0px;
        padding-right: 12px;
        border-radius: 30px;
        background-color: white;
        border-style:none;
	}

	svg.searchActive{
		cursor: pointer;
	}

	#circle, #negLine, #posLine{
		transition: 0.3s ease-in-out;
	}

	#circle.searchActive{
		transform: scale(1.4) translateX(-30px) translateY(-15px);
	}

	#negLine.searchActive{
		transform: translate(-91px, -78px);
	}

	#posLine{
		opacity: 0.0;
	}

	#posLine.searchActive{
		transform-origin: center;
		transform: translate(+73px, -83px) rotate(90deg);
		opacity: 1.0;
	}

	#search-field {
		width: 100%;
		font-size: 1rem;		
		padding: 12px;
		margin: 0 10px 0;
        border-width: 0px;
        border-style:none;
        border-radius: 30px;
	}

	#search-field:focus {
		width: 100%;
		font-size: 1rem;		
		padding: 12px;
		margin: 0 10px 0;
        border-width: 0px;
        border-style:none;
        border-radius: 30px;
	}
</style>