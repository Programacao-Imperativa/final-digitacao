<script lang="ts">
import { frases } from './text';
import NavBottom from '../../components/NavBottom.svelte';


let indice: number = 0;
let ifrase: number = 0;
let textFull = '';
let frase = frases[ifrase];
let caracteres: string[] = frase.text.split('');
let currentIndex: number = 0;
let pressedKey: string = '';

function nextText(): void { 
	if (ifrase >= frases.length - 1) {
		ifrase = 0;
	} else {
		ifrase++;
	}
	indice = 0;
	textFull = '';
	frase = frases[ifrase];
	caracteres = frase.text.split('');
	currentIndex = 0;
}

function handleKeydown(event: KeyboardEvent): void {
	pressedKey = event.key;
	if (caracteres[currentIndex] === pressedKey) {
		textFull += caracteres[currentIndex];
		currentIndex++;
		if (currentIndex >= caracteres.length) {
			console.log('Frase completa');
		}
	} else {
		console.log('Errado: ' + pressedKey);
	}
}
</script>

<svelte:window on:keydown={handleKeydown} />

<div class="title">
	<h1>Jogo da Digitação</h1>
</div>

<div class="text">
	<p class="text">{frase.text}</p>
	<p class="input">{textFull}</p>
</div>

<div class="next">
	<button class="btn" on:click={nextText}>Próxima</button>
</div>

<NavBottom />

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
		width: 90%;
		height: 80vh;
		top: 23%;
		text-align: left;
		font-size: 2rem;
		color: #928e8e;
		margin-left: 4rem;
	}

	.input {
		position: absolute;
		height: 80vh;
		width: 90%;
		top: 23%;
		text-align: left;
		font-size: 2rem;
		margin-left: 4rem;
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
