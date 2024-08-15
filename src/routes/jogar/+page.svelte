<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import { frases } from './text';

	let indice: number = 0;
	let ifrase: number = 0;
    let textFull = '';
	let frase = frases[ifrase];

	function nextText(): void { 

		if (indice >= frases.length - 1) {
			indice = 0;
		} else {
			indice++;
			ifrase++;
			textFull = '';
		}
		frase = frases[indice];

	}

	const caracteres: string[] = frase.text.split('');

	let currentIndex: number = 0;

	let pressedKey: string = '';

	function handleKeydown(event: KeyboardEvent): void {
		pressedKey = event.key;
		console.log(caracteres[currentIndex]);
		if (caracteres[currentIndex] ===  pressedKey) {
			console.log('Correto: ' + caracteres[currentIndex]);
            console.log('teste:'+textFull);

			textFull = textFull + caracteres[currentIndex];
			currentIndex++;
			if (currentIndex >= caracteres.length) {
				currentIndex = 0;
				console.log('Frase completa');
			}
		} else {
			console.log('Errado: ' + pressedKey);
		}
	}

	onMount(() => {
		window.addEventListener('keydown', handleKeydown);
	});

	onDestroy(() => {
		window.removeEventListener('keydown', handleKeydown);
	});
</script>

<div class="title">
	<h1>Jogo da Digitação</h1>
</div>

<div class="text">
	<p class="text">{frase.text}</p>
	<p class="entrada">{textFull}</p>
</div>

<div class="next">
	<button class="btn" on:click={nextText}>Próxima</button>
</div>

<style scoped>
	* {
		overflow: hidden;
	}

	.title {
		position: absolute;
		top: 0;
		width: 100%;
		text-align: center;
		font-size: 1.5rem;
		color: #928e8e;
	}

	.text {
		position: absolute;
		width: 5rem;
		height: 80vh;
		width: 100%;
		top: 23%;
		text-align: left;
		font-size: 2rem;
		color: #928e8e;
		margin-left: 5rem;
	}

	.entrada {
		position: absolute;
		height: 80vh;
		width: 100%;
		top: 23%;
		text-align: left;
		font-size: 2rem;
		margin-left: 5rem;
		color: #fff;
	}

	.btn {
		position: absolute;
		top: 70%;
		background-color: #171a17;
		border: none;
		color: white;
		padding: 15px 32px;
		text-align: center;
		text-decoration: none;
		display: inline-block;
		font-size: 16px;
		margin: 4px 2px;
		cursor: pointer;
		border-radius: 20px;
	}

	.next {
		width: 100%;
		text-align: center;
		font-size: 1.5rem;
		color: #928e8e;
	}
</style>
