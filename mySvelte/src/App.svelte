<script>
	import home from './home.svelte';
	import Router from 'svelte-spa-router';
	import Header from './Header.svelte';

	let name = 'world';
	let age = 85;
	let fruits = ['Apple','Banana','Cherry','Orange']
	let toggle = false
	
	function assign() {
		name = 'Donghyun'
		age = 36
	}
	
	function deleteFruit() {
		fruits = fruits.slice(1)
	}
	
	if (toggle) {
	} else {
	}	
	
	let isRed = false
	
	function enter() {
		name = 'enter'
	}
	function leave() {
		name = 'leave'
	}
	
	const routes = {
    '/': home,
  };
</script>

<button on:click={() => {toggle = !toggle}}>
	Toggle
</button>

{#if toggle}
	<h1>Hello {name}! </h1>
	{:else}
<div> No name! </div>
{/if}

<h2 class={age < 85 ? 'active' : ''}>
	{age}
</h2>

<img src="" alt={name} />

<input type="text" bind:value={name} />

<button on:click={assign}> Assign </button> 

<div class="box" 
		 style="background-color: {isRed ? 'red' : 'orange'};" 
		 on:click={() => { isRed = !isRed}}
	on:mouseenter={enter}
	on:mouseleave={leave}>
	Box!</div>

<ul>
	{#each fruits as fruit}
		<li>{fruit}</li>
	{/each}
</ul>
<button on:click={deleteFruit}>
	Eat it!
</button>

<main>
	<Header />
  <Router {routes} />
</main>


<style>
	h1 {
		color : red;
	}
	.active {
		color: blue;
	}

	.box {
		width: 300px;
		height: 150px;
		background-color: orange;
}
</style>