<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import Row from '$lib/Containers/Row.svelte';

	import { onMount } from 'svelte';
	import { dark } from '../../ui_store';
	import Icon from '$lib/Graphics/Icon.svelte';

	let start: boolean = false;
	let pause: boolean = false;
	let startText = 'Start';
	let totalHours = 0;
	let totalMinutes = 25;
	let trackerSeconds = 0;
	let workingTime = 25;
	let trackedWorkingTime = 0;
	let breakTime = 5;
	let trackedBreakTime = 0;
	let numberOfPauses = 0;
	let numberOfBreaks = 0;
	let completed: boolean = false;

	function updateClock(
		hourHandOne: HTMLElement,
		minuteHandOneInner: HTMLElement,
		minuteHandOne: HTMLElement,
		minuteHandTwo: HTMLElement,
		minuteHandThree: HTMLElement
	) {
		const now = new Date();
		const seconds = now.getSeconds();
		const minutes = now.getMinutes();
		const hours = now.getHours();
		if (start && !completed) {
			if (trackerSeconds == totalHours * 60 * 60 + totalMinutes * 60) {
				alert('Congrats, you completed two minutes of work!');
				completed = true;
			} else {
				if (trackedWorkingTime / 60 < workingTime) {
					const minuteDegreesOne = (minutes / 60) * 360 + (seconds / 60) * 6;
					const hourDegrees = (hours / 12) * 360 + (minutes / 60) * 30;

					if (!pause) {
						trackerSeconds = trackerSeconds + 1;

						trackedWorkingTime = trackedWorkingTime + 1;

						minuteHandOneInner.style.transform = `rotate(${minuteDegreesOne}deg)`;
						minuteHandOne.style.transform = `rotate(${minuteDegreesOne}deg)`;
						hourHandOne.style.transform = `rotate(${hourDegrees}deg)`;
					} else {
						const minuteDegreesOne = (minutes / 60) * 360 + (seconds / 60) * 6;
						const minuteDegreesTwo =
							((minutes + workingTime - trackedWorkingTime / 60) / 60) * 360 + (seconds / 60) * 6;
						const minuteDegreesThree =
							((minutes + workingTime - trackedWorkingTime / 60 + breakTime) / 60) * 360 +
							(seconds / 60) * 6;
						const hourDegrees = (hours / 12) * 360 + (minutes / 60) * 30;

						minuteHandOneInner.style.transform = `rotate(${minuteDegreesOne}deg)`;
						minuteHandOne.style.transform = `rotate(${minuteDegreesOne}deg)`;
						minuteHandTwo.style.transform = `rotate(${minuteDegreesTwo}deg)`;
						minuteHandThree.style.transform = `rotate(${minuteDegreesThree}deg)`;
						hourHandOne.style.transform = `rotate(${hourDegrees}deg)`;
					}
				} else if (trackedBreakTime / 60 < breakTime) {
					const minuteDegreesOne = (minutes / 60) * 360 + (seconds / 60) * 6;
					const minuteDegreesTwo = (minutes / 60) * 360 + (seconds / 60) * 6;
					const hourDegrees = (hours / 12) * 360 + (minutes / 60) * 30;

					if (!pause) {
						trackedBreakTime = trackedBreakTime + 1;

						minuteHandOneInner.style.transform = `rotate(${minuteDegreesOne}deg)`;
						minuteHandOne.style.transform = `rotate(${minuteDegreesOne}deg)`;
						minuteHandTwo.style.transform = `rotate(${minuteDegreesTwo}deg)`;
						hourHandOne.style.transform = `rotate(${hourDegrees}deg)`;
					} else {
						const minuteDegreesOne = (minutes / 60) * 360 + (seconds / 60) * 6;
						const minuteDegreesTwo =
							((minutes + workingTime - trackedWorkingTime / 60) / 60) * 360 + (seconds / 60) * 6;
						const minuteDegreesThree =
							((minutes +
								workingTime -
								trackedWorkingTime / 60 +
								breakTime -
								trackedBreakTime / 60) /
								60) *
								360 +
							(seconds / 60) * 6;
						const hourDegrees = (hours / 12) * 360 + (minutes / 60) * 30;

						minuteHandOneInner.style.transform = `rotate(${minuteDegreesOne}deg)`;
						minuteHandOne.style.transform = `rotate(${minuteDegreesOne}deg)`;
						minuteHandTwo.style.transform = `rotate(${minuteDegreesTwo}deg)`;
						minuteHandThree.style.transform = `rotate(${minuteDegreesThree}deg)`;
						hourHandOne.style.transform = `rotate(${hourDegrees}deg)`;
					}
				} else {
					numberOfBreaks = numberOfBreaks + 1;

					const minuteDegreesOne = (minutes / 60) * 360 + (seconds / 60) * 6;
					const minuteDegreesTwo = ((minutes + workingTime) / 60) * 360 + (seconds / 60) * 6;
					const minuteDegreesThree =
						((minutes + workingTime + breakTime) / 60) * 360 + (seconds / 60) * 6;
					const hourDegrees = (hours / 12) * 360 + (minutes / 60) * 30;

					trackedWorkingTime = 0;
					trackedBreakTime = 0;

					minuteHandOneInner.style.transform = `rotate(${minuteDegreesOne}deg)`;
					minuteHandOne.style.transform = `rotate(${minuteDegreesOne}deg)`;
					minuteHandTwo.style.transform = `rotate(${minuteDegreesTwo}deg)`;
					minuteHandThree.style.transform = `rotate(${minuteDegreesThree}deg)`;
					hourHandOne.style.transform = `rotate(${hourDegrees}deg)`;
				}
			}
		} else {
			if (!completed) {
				trackedWorkingTime = 0;
				trackedBreakTime = 0;

				const minuteDegreesOne = (minutes / 60) * 360 + (seconds / 60) * 6;
				const minuteDegreesTwo = ((minutes + workingTime) / 60) * 360 + (seconds / 60) * 6;
				const minuteDegreesThree =
					((minutes + workingTime + breakTime) / 60) * 360 + (seconds / 60) * 6;
				const hourDegrees = (hours / 12) * 360 + (minutes / 60) * 30;

				minuteHandOneInner.style.transform = `rotate(${minuteDegreesOne}deg)`;
				minuteHandOne.style.transform = `rotate(${minuteDegreesOne}deg)`;
				minuteHandTwo.style.transform = `rotate(${minuteDegreesTwo}deg)`;
				minuteHandThree.style.transform = `rotate(${minuteDegreesThree}deg)`;
				hourHandOne.style.transform = `rotate(${hourDegrees}deg)`;
			}
		}
	}

	function updateStart() {
		pause = start ? !pause : pause;
		start = true;
		startText = pause ? 'Resume' : 'Pause';
		numberOfPauses = pause ? numberOfPauses + 1 : numberOfPauses;
	}

	function reset() {
		start = pause = false;
		startText = 'Start';
		trackedWorkingTime = trackedBreakTime = trackerSeconds = 0;

		numberOfPauses = 0;
		numberOfBreaks = 0;

		completed = false;
	}

	onMount(() => {
		const hourHandOne = document.getElementById('hourHandOne');
		const minuteHandOneInner = document.getElementById('minuteHandOneInner');
		const minuteHandOne = document.getElementById('minuteHandOne');
		const minuteHandTwo = document.getElementById('minuteHandTwo');
		const minuteHandThree = document.getElementById('minuteHandThree');

		if (hourHandOne && minuteHandOneInner && minuteHandOne && minuteHandTwo && minuteHandThree) {
			setInterval(
				updateClock,
				1000,
				hourHandOne,
				minuteHandOneInner,
				minuteHandOne,
				minuteHandTwo,
				minuteHandThree
			);
			updateClock(hourHandOne, minuteHandOneInner, minuteHandOne, minuteHandTwo, minuteHandThree);
		}
	});
</script>

<svelte:head>
	<title>Dalton Blake | 25 + 5</title>

	<meta
		name="description"
		content="Boost your productivity with the 25+5 Method, a web tool designed to optimize work and break cycles. Track your time effectively with customizable work sessions and breaks to maintain focus and recharge throughout the day."
	/>
</svelte:head>

<Column dark={$dark} gap="75px" minwidth="100%" maxwidth="100%">
	<Row
		grow="0"
		background="transparent"
		alignitems="center"
		justifycontent="center"
		wrap="flex-wrap"
		minwidth="100%"
		maxwidth="100%"
	>
		<header class="header">
			<h1 style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'};" class="title">
				Focus & Recharge: The 25+5 Method
			</h1>
			<p class="subtitle">Maximize your productivity with balanced work & break cycles</p>
		</header>
	</Row>

	<!-- Clock Display -->
	<Row
		grow="0"
		background="transparent"
		alignitems="center"
		justifycontent="center"
		wrap="flex-wrap"
		minwidth="100%"
		maxwidth="100%"
		margin="0 0 0 0"
	>
		<div class="clock {$dark ? 'dark-clock' : ''}">
			<!-- Clock Hands -->
			<div id="hourHandOne" class="hour-hand-outer {$dark ? 'dark-hand' : ''}"></div>
			<div id="minuteHandOneInner" class="minute-hand-inner-one {$dark ? 'dark-hand' : ''}"></div>
			<div id="minuteHandOne" class="minute-hand-outer-one {$dark ? 'dark-hand' : ''}"></div>
			<div id="minuteHandTwo" class="minute-hand-outer-two {$dark ? 'dark-hand' : ''}"></div>
			<div id="minuteHandThree" class="minute-hand-outer-three {$dark ? 'dark-hand' : ''}"></div>
			<div class="center-circle {$dark ? 'dark-hand' : ''}">&nbsp;</div>

			<!-- <svg class="time-circle-container" viewBox="0 0 100 100">
				Dynamic Time Circle
				<circle cx="50" cy="50" r="45" class="time-circle"></circle>
			  </svg> -->

			<!-- Clock Numbers -->
			{#each Array.from({ length: 12 }, (_, i) => i + 1) as number, index}
				<div class="number {$dark ? 'dark-number' : ''}" style="--rotation: {30 * (index + 1)};">
					{index === 11 ? 12 : 11 - index}
				</div>
			{/each}

			<!-- Overlay -->
			<div class="hide-outer-clocks {$dark ? 'dark-hide' : ''}">&nbsp;</div>
		</div>
	</Row>

	<!-- Interactive Sentence -->
	<Row
		grow="0"
		justifycontent="center"
		wrap="flex-wrap"
		minwidth="100%"
		maxwidth="100%"
		background="transparent"
		margin="-25px 0 0 0"
	>
		<div class="interactive-sentence">
			<!-- Hour Input -->
			<span
				style="transition: all 150ms; white-space: nowrap; color: {$dark
					? 'var(--darktext)'
					: 'var(--primary)'};">I would like to work for&nbsp;</span
			>
			<input
				disabled={start}
				type="number"
				placeholder="0"
				min="0"
				max="24"
				class={$dark ? 'dark-input' : ''}
				bind:value={totalHours}
			/>
			<span
				style="transition: all 150ms; white-space: nowrap; color: {$dark
					? 'var(--darktext)'
					: 'var(--primary)'};">&nbsp;hours and&nbsp;</span
			>

			<!-- Minutes Input -->
			<input
				disabled={start}
				type="number"
				placeholder="0"
				min="0"
				max="59"
				class={$dark ? 'dark-input' : ''}
				bind:value={totalMinutes}
			/>
			<span
				style="transition: all 150ms; white-space: nowrap; color: {$dark
					? 'var(--darktext)'
					: 'var(--primary)'};">&nbsp;minutes with&nbsp;</span
			>

			<!-- Working Time Input -->
			<input
				disabled={start}
				type="number"
				placeholder="0"
				min="1"
				max="60"
				class={$dark ? 'dark-input' : ''}
				bind:value={workingTime}
			/>
			<span
				style="transition: all 150ms; white-space: nowrap; color: {$dark
					? 'var(--darktext)'
					: 'var(--primary)'};">&nbsp;minute working sessions and&nbsp;</span
			>

			<!-- Break Time Input -->
			<input
				disabled={start}
				type="number"
				placeholder="0"
				min="1"
				max="45"
				class={$dark ? 'dark-input' : ''}
				bind:value={breakTime}
			/>
			<span style="white-space: nowrap; color: {$dark ? 'var(--darktext)' : 'var(--primary)'};"
				>&nbsp;minute breaks.</span
			>
		</div>
	</Row>

	<!-- Buttons -->
	<Row
		grow="0"
		justifycontent="center"
		gap="10px"
		minwidth="100%"
		background="transparent"
		margin="-25px 0 0 0"
	>
		<button
			id="toggle-button"
			class="toggle-button {$dark ? 'dark-button' : ''}"
			on:click={updateStart}
		>
			{#if startText == 'Start' || startText == 'Resume'}
				<Icon
					color={$dark ? 'var(--darktext)' : 'var(--darktext)'}
					icon="fa-light fa-play"
					size="fa-lg"
					margin="0 5px 0 0"
				></Icon>
			{:else}
				<Icon
					color={$dark ? 'var(--darktext)' : 'var(--darktext)'}
					icon="fa-light fa-pause"
					size="fa-lg"
					margin="0 5px 0 0"
				></Icon>
			{/if}
			{startText}
		</button>

		<button id="reset-button" class="toggle-button {$dark ? 'dark-button' : ''}" on:click={reset}>
			<Icon
				color={$dark ? 'var(--darktext)' : 'var(--darktext)'}
				icon="fa-light fa-arrows-rotate-reverse"
				size="fa-lg"
				margin="0 5px 0 0"
			></Icon>
			Reset
		</button>
	</Row>

	<!-- Stats Table -->
	<Row
		grow="0"
		justifycontent="center"
		gap="10px"
		minwidth="100%"
		background="transparent"
		margin="-25px 0 50px 0"
	>
		<div class="table-container">
			<table class="stats-table {$dark ? 'dark-table' : ''}">
				<thead>
					<tr>
						<th>Time Worked</th>
						<th>Number of Pauses</th>
						<th>Number of Breaks</th>
					</tr>
				</thead>
				<tbody>
					<tr>
						<td
							>{Math.floor(trackerSeconds / 60 / 60)
								.toString()
								.padStart(2, '0')}:{Math.floor(trackerSeconds / 60)
								.toString()
								.padStart(2, '0')}:{(trackerSeconds % 60).toString().padStart(2, '0')}</td
						>
						<td>{numberOfPauses}</td>
						<td>{numberOfBreaks}</td>
					</tr>
				</tbody>
			</table>
		</div>
	</Row>
</Column>

<style type="text/css">
	/* === Header Styling === */
	.header {
		border-radius: 10px;
		padding: 0 20px;
		transition: all 150ms;
	}

	.title {
		font-size: 2.5rem;
		font-weight: bold;
		color: var(--primary); /* Green accent color */
		margin-bottom: 10px;
		text-transform: uppercase;
		letter-spacing: 2px;
		animation: slideIn 1s ease-out;
		transition: all 150ms;
	}

	.subtitle {
		font-size: 1.2rem;
		color: #666;
		margin-top: 10px;
		font-style: italic;
		transition: all 150ms;
	}

	@keyframes slideIn {
		from {
			opacity: 0;
			transform: translateY(-30px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@media (max-width: 768px) {
		.title {
			font-size: 2rem;
		}
		.subtitle {
			font-size: 1.2rem;
		}
	}

	@media (max-width: 480px) {
		.title {
			font-size: 1.5rem;
		}
		.subtitle {
			font-size: 1rem;
		}
	}

	/* === Clock Styling === */
	.clock {
		position: relative;
		width: 250px;
		height: 250px;
		background: #ffffff;
		border-radius: 50%;
		border: 5px solid;
		border-color: var(--primary);
		box-shadow: rgba(0, 0, 0, 0.5) 0px 5px 5px 0px;
		transition: all 150ms;
	}

	.dark-clock {
		background: var(--primary);
		border-color: var(--darktext);
	}

	.time-circle-container {
		position: absolute;
		top: -15px;
		left: -15px;
		height: calc(100% + 30px);
		width: calc(100% + 30px);
	}

	.time-circle {
		fill: none;
		stroke: #00aaff;
		stroke-width: 10;
		stroke-dasharray: 283; /* Circumference of the circle (2 * π * r) */
		stroke-dashoffset: 300; /* Initially hide the circle */
		transition: stroke-dashoffset 0.3s ease;
		z-index: 8;
	}

	.number {
		position: absolute;
		font-size: 1.2em;
		font-weight: bold;
		color: #333;
		transform: translate(-50%, -50%) rotate(calc(var(--rotation) * -1deg));
		transform-origin: 50% 120px;
		transition: color 150ms;
		z-index: 5;
	}

	.dark-number {
		color: var(--darktext);
	}

	.number:nth-child(n) {
		top: 16px;
		left: 125px;
	}

	/* === Input Styling === */
	.interactive-sentence {
		display: flex;
		align-items: center;
		white-space: pre-wrap;
		padding: 0 20px;
		width: calc(100% - 40px);
		flex-wrap: wrap;
		justify-content: center;
	}

	@media (max-width: 768px) {
		.interactive-sentence {
			font-size: 12px;
		}
	}

	@media (max-width: 480px) {
		.interactive-sentence {
			font-size: 12px;
		}
	}

	input {
		padding: 12px 10px;
		font-size: 16px;
		color: #333;
		background: transparent;
		border: none;
		border-bottom: 2px solid #ccc;
		outline: none;
		transition: all 150ms ease;
	}

	input:focus {
		border-bottom: 2px solid var(--primary);
	}

	.dark-input {
		color: var(--darktext);
	}

	/* === Input Container Animation === */
	.input-container::after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 0;
		width: 0%;
		height: 2px;
		background-color: var(--primary);
		transition: width 150ms ease;
	}

	/* === Clock Hands Styling === */
	.hour-hand-outer,
	.minute-hand-inner-one,
	.minute-hand-outer-one,
	.minute-hand-outer-two,
	.minute-hand-outer-three {
		position: absolute;
		width: 5px;
		background: var(--primary);
		border-radius: 5px;
		transform-origin: bottom center;
		transition: all 150ms;
	}

	.hour-hand-outer {
		height: 70px;
		top: 55px;
		left: calc(50% - 2px);
		transform: rotate(90deg);
		z-index: 6;
	}

	.center-circle {
		position: absolute;
		top: calc(50% - 5px);
		left: calc(50% - 5px);
		border-radius: 50%;
		height: 10px;
		width: 10px;
		background: var(--primary);
		z-index: 6;
		transition: all 150ms;
	}

	.dark-hand {
		background: var(--darktext);
	}

	.minute-hand-outer-one,
	.minute-hand-outer-two,
	.minute-hand-outer-three {
		height: 147px;
		top: -23px;
		left: calc(50% - 2px);
		transform: rotate(0deg);
	}

	.minute-hand-inner-one {
		height: 115px;
		top: 9px;
		left: calc(50% - 2px);
		transform: rotate(0deg);
		z-index: 6;
	}

	.minute-hand-outer-three {
		z-index: 3;
	}

	/* === Clock Face Overlay === */
	.hide-outer-clocks {
		position: absolute;
		width: 100%;
		height: 100%;
		background: white;
		border-radius: 50%;
		z-index: 4;
		transition: all 150ms;
		top: -5px;
		left: -5px;
		border: 5px solid;
		border-color: var(--primary);
	}

	.dark-hide {
		background: var(--primary);
		border-color: var(--darktext);
	}

	/* === Button Styling === */
	.toggle-button {
		padding: 10px 20px;
		font-size: 16px;
		color: white;
		background-color: var(--primary);
		border: none;
		border-radius: 5px;
		cursor: pointer;
		transition: background-color 150ms ease;
	}

	.toggle-button:hover {
		background-color: #7d0000;
	}

	.dark-button {
		background-color: #444;
		color: var(--darktext);
	}

	.dark-button:hover {
		background-color: #555;
	}

	/* === Table Styling === */
	.table-container {
		border-radius: 5px;
		overflow-x: auto;
		margin-top: 20px;
		padding: 0 10px;
	}

	.stats-table {
		width: 100%;
		background-color: #fff;
		border-radius: 8px;
		border: solid 1px var(--primary);
		border-radius: 5px;
		border-spacing: 0;
	}

	.dark-table {
		background-color: #333;
	}

	.stats-table th,
	.stats-table td {
		padding: 12px 15px;
		text-align: center;
		border: none;
	}

	.stats-table th {
		background-color: var(--primary);
		color: white;
		font-weight: normal;
	}

	.stats-table td {
		border-radius: 5px;
		color: #333;
	}

	.dark-table td {
		border-radius: 5px;
		color: var(--darktext);
	}

	.stats-table tr:nth-child(even) td {
		background-color: #f1f1f1;
	}

	@media screen and (max-width: 600px) {
		.stats-table {
			font-size: 12px;
		}

		.stats-table th,
		.stats-table td {
			padding: 8px 10px;
		}
	}
</style>
