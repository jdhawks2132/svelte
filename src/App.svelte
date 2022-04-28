<script>
	import Modal from './Modal.svelte';

	let showModal = false;

	const toggleModal = () => {
		showModal = !showModal;
	};

	let people = [
		{ id: 1, name: 'John', age: 21, beltColor: 'black' },
		{ id: 2, name: 'Mary', age: 22, beltColor: 'blue' },
		{ id: 3, name: 'Bob', age: 23, beltColor: 'red' },
		{ id: 4, name: 'Peter', age: 24, beltColor: 'green' },
		{ id: 5, name: 'Sara', age: 25, beltColor: 'yellow' },
		{ id: 6, name: 'Paul', age: 26, beltColor: 'brown' },
		{ id: 7, name: 'Jane', age: 27, beltColor: 'purple' },
		{ id: 8, name: 'Mark', age: 28, beltColor: 'pink' },
		{ id: 9, name: 'Linda', age: 29, beltColor: 'orange' },
		{ id: 10, name: 'John', age: 30, beltColor: 'black' },
	];

	const handleClick = (id) => {
		people = people.filter((person) => person.id !== id);
	};
</script>

<Modal message="Hey, I am a prop" isPromo={true} {showModal} on:click={toggleModal} />

<main>
	<button on:click={toggleModal}>Open Modal</button>
	<div>
		{#each people as person (person.id)}
			<div>
				<h2>{person.name}</h2>
				{#if person.beltColor == 'black'}
					<p><strong>MASTER NINJA</strong></p>
				{/if}
				<p>{person.age} years old</p>
				<p>{person.beltColor} belt</p>
				<button on:click={() => handleClick(person.id)}>Delete</button>
			</div>
		{:else}
			<p>No people found</p>
		{/each}
	</div>
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
