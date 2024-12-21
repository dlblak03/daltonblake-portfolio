<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import { onMount } from 'svelte';
	import { dark } from '../ui_store';

	const text = ['Working on it.. '];
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
			isDeleting = false;
			setTimeout(typeText, pauseBetweenTexts); // Pause before deleting
			return;
		}

		if (isDeleting && currentCharIndex === 0) {
			isDeleting = false;
		}

		setTimeout(typeText, isDeleting ? deletingSpeed : typingSpeed);
	}

	onMount(() => {
		typeText();
	});
</script>

<Column dark={$dark} alignitems="center" justifycontent="center" minwidth="100%">
	<div id="typing-container">
		<span
			style="color: {$dark
				? 'var(--darktext)'
				: 'var(--primary)'}; letter-spacing: 0.2rem; text-align: center;"
			id="typing-text">{textVariable}</span
		>
		<span style="color: {$dark
        ? 'var(--darktext)'
        : 'var(--primary)'};" id="cursor">|</span>
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
