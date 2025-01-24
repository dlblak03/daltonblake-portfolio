<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import Row from '$lib/Containers/Row.svelte';
	import Icon from '$lib/Graphics/Icon.svelte';

	import { dark } from './ui_store';
	import { onMount } from 'svelte';

	const text = [
		'Hello, welcome to my website.. ',
		'Explore cool projects.. ',
		'Or connect with me on social media. '
	];
	let currentTextIndex = 0;
	let currentCharIndex = 0;
	let isDeleting = false;
	const typingSpeed = 100; // Speed of typing (ms)
	const deletingSpeed = 75; // Speed of deleting (ms)
	const pauseBetweenTexts = 2000; // Pause before typing new text
	let textVariable = '';

	function typeText() {
		const currentText = text[currentTextIndex];

		if (isDeleting) {
			textVariable = currentText.slice(0, currentCharIndex--);
		} else {
			textVariable = currentText.slice(0, currentCharIndex++);
		}

		if (!isDeleting && currentCharIndex === currentText.length) {
			isDeleting = true;
			setTimeout(typeText, pauseBetweenTexts); // Pause before deleting
			return;
		}

		if (isDeleting && currentCharIndex === 0) {
			isDeleting = false;
			currentTextIndex = (currentTextIndex + 1) % text.length; // Move to next text
		}

		setTimeout(typeText, isDeleting ? deletingSpeed : typingSpeed);
	}

	onMount(() => {
		
	});
</script>

<svelte:head>
	<title>Dalton Blake</title>

	<meta
		name="description"
		content="Explore the development projects of Dalton Blake, showcasing innovative solutions built with modern technologies. Discover the portfolio of a skilled developer dedicated to creating impactful, user-centered digital experiences."
	/>
</svelte:head>

<Column justifycontent="center" alignitems="center" minwidth="100%" dark={$dark}>
	<Row grow="0" dark={$dark} justifycontent="center" alignitems="center" padding="0 20px">
		<div id="typing-container">
			<span
				style="color: {$dark
					? 'var(--darktext)'
					: 'var(--primary)'}; letter-spacing: 0.2rem; text-align: center;"
				id="typing-text">Heyo, I'm Dalton. Learning and creating innovative products is my passion.</span
			>
		</div>
	</Row>

	<div
		style="margin-top: 50px; display: flex; align-items: center; width: 125px; height: 35px; gap: 10px; background: var(--primary); padding: 10px 10px; border-radius: 5px;"
	>
		<Row
			cursor="pointer"
			on:click={() => {
				window.open('https://www.linkedin.com/in/daltonblake05/', '_blank');
			}}
			background="transparent"
			alignitems="center"
			justifycontent="center"
		>
			<Icon
				color={$dark ? 'var(--darktext)' : 'var(--darktext)'}
				icon="fa-brands fa-linkedin"
				size="fa-xl"
			></Icon>
		</Row>
		<Row
			cursor="pointer"
			on:click={() => {
				window.open('https://github.com/dlblak03', '_blank');
			}}
			background="transparent"
			alignitems="center"
			justifycontent="center"
		>
			<Icon
				color={$dark ? 'var(--darktext)' : 'var(--darktext)'}
				icon="fa-brands fa-github"
				size="fa-xl"
			></Icon>
		</Row>
		<Row
			cursor="pointer"
			on:click={() => {
				window.open('https://codepen.io/dlblak03', '_blank');
			}}
			background="transparent"
			alignitems="center"
			justifycontent="center"
		>
			<Icon
				color={$dark ? 'var(--darktext)' : 'var(--darktext)'}
				icon="fa-brands fa-codepen"
				size="fa-xl"
			></Icon>
		</Row>
	</div>
</Column>

<style>
	#typing-container {
		font-size: 20px;
		display: inline-block;
		text-align: center;
		overflow: hidden;
		white-space: pre-wrap;
	}

	#cursor {
		display: inline-block;
		animation: blink 0.7s step-end infinite;
	}

	@keyframes blink {
		from,
		to {
			opacity: 1;
		}
		50% {
			opacity: 0;
		}
	}
</style>
