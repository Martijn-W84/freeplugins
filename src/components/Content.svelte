<script>
    export let plugins;
    export let categories;
    import FilterSection from "./FilterSection.svelte";
    import Grid from "./Grid.svelte";
    import Search from "./Search.svelte";
    import Sidebar from "./Sidebar.svelte";

    let sidebar_show = false;
    let filterTerm = "ALL";
    let searchTerm = "";
    let elm;

    const clearSearch = () => {
        searchTerm = "";        
        elm.focus();        
    }

    const filterSelection = (e) => {
        filterTerm = e.target.dataset.name.toUpperCase();
        sidebar_show = false;   
    }

    const clearFilter= () => {
        filterTerm = "ALL";     
    }
</script>

<Sidebar bind:show={sidebar_show} on:click={filterSelection} categories={categories} {filterTerm}></Sidebar>
<div id="filter-container">
    <Search bind:searchTerm bind:elm on:click={() => (clearSearch())} on:keyup={() => (clearSearch())}/>
    <FilterSection {filterTerm} bind:sidebar_show={sidebar_show}  on:click={() => (clearFilter())} on:keyup={() => (clearFilter())}></FilterSection>
</div>
<Grid {plugins} {filterTerm} {searchTerm}></Grid>

<style>
    #filter-container{
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        margin-bottom: 20px;
    }
</style>
