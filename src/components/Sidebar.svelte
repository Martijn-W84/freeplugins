<script>
  export let show = false;
  export let categories;
  export let filterTerm;
 
</script>
  <nav class="transition" class:show={show}>
    <div class="button-container">
      {#each categories as category}        
        <button class="item btn" 
                class:active={filterTerm.toUpperCase() === category.toUpperCase()}
                data-name={category}
                on:click>
                {category.toUpperCase()}
        </button>
      {/each}
    </div>
  </nav>

<style>
  nav {
    position: fixed;
    top: 60px;
    right: 0;
    height: calc( 100dvh   - 60px );
    background: #fff;
    overflow-y: auto;
    width: 100%;
    z-index: 10;
    transition: 200ms;
    transition-timing-function: ease-in-out;
  }

  .button-container{
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(10, 1fr);
    grid-auto-flow: column; 
  }

  @media (min-height: 700px) {
    nav { 
      width: 12rem; 
      box-shadow: rgba(100, 100, 111, 0.3) 0px 7px 29px 0px;
    }

    .button-container {
      grid-template-columns: repeat(1, 1fr); 
      grid-template-rows: repeat(19, 1fr);
    }
  }

  .btn {
    border: none;
    outline: none;
    padding: 12px 12px;
    background-color: #fff;
    cursor: pointer;
    transition-duration: 250ms;
    border-radius: 20px;
    margin: 5px;
    font-family: Lato;
    font-size: medium;
  }

  .btn:hover {  
    background-color: #D7DAE2;
  }

  .btn.active {
    background-color: #070821;
    color: white;
  }

  .transition {
		visibility: hidden;
		transform: translateX(100px);
		opacity: 0;
		transition: opacity 0.3s, transform 0.3s, visibility 0s 0.3s;
	}
	.transition.show {
		visibility: visible;
		opacity: 1;
		transform: scale(1);
		transition: opacity 0.3s, transform 0.3s;
	}
</style>