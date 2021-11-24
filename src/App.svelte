<script>

	import Modal from './Modal.svelte'
	import AddPersonForm from './AddPersonForm.svelte'
	
	 let name = "Sergiu";
	 let hello = "Hello";
	 let showModal = false

	 let people = [
		 {person: 'Person1', desc: 'Description1', age: 1, id: 1},
		 {person: 'Person2', desc: 'Description2', age: 2, id: 2},
		 {person: 'Person3', desc: 'Description3', age: 3, id: 3},
	 ];

	 const handleChange = () => {
		 name = "Vasea";
	 };

	 const handleDelete = (id) => {
		people = people.filter((person) => person.id != id);
	 };

	 const toggleModal = () => {
		 showModal = !showModal
	 }

	//  const handleInput = (e) => {
	// 	name = e.target.value;
	//  };
</script>
<Modal {showModal}>
	<h3>Add a new Person</h3>
	<AddPersonForm />
</Modal>
<main>

	<button on:click ={toggleModal}>Open Modal</button>

	<h1>Hello {name}!</h1>
	<p style="color: {hello}">{hello} Svelte</p>
	<button on:click={handleChange}>Click me to change</button>
	<input type="text" bind:value={hello}>

	{#each people as percon(percon.id)}
		<h2>{percon.person}</h2>
		<p>{percon.desc}</p>
		{#if percon.desc === 'Description2'}
			<h3>Master Sergiu</h3>
		{/if}
		<p>{percon.age}</p>
		<button on:click={() => {handleDelete(percon.id)}}>Delete</button>
	{:else}
		<p>Not Persons</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>