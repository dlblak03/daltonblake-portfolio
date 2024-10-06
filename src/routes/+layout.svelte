<!-- src/routes/+layout.svelte -->
<script lang="ts">
	import { invalidate } from '$app/navigation';
	import { onMount } from 'svelte';

	import { dark } from './ui_store';

	import Column from '$lib/Containers/Column.svelte';
	import Row from '$lib/Containers/Row.svelte';
	import Dialog from '$lib/Containers/Dialog.svelte';

	import ButtonPrimary from '$lib/Buttons/ButtonPrimary.svelte';

	import P from '$lib/Text/P.svelte';
	import Icon from '$lib/Graphics/Icon.svelte';

	let menuToggle: boolean = false;
	let aboutDialog: boolean = false;

	export let data;

	let savestore = false;
	$: if (savestore) {
		setCookie('dark', $dark, 1);
	}

	onMount(() => {
		let darkCookie = getCookie('dark');
		if (darkCookie) {
			$dark = darkCookie === 'true' ? true : false;
		}
		savestore = true;

		return () => {};
	});

	const toggleDark = async () => {
		$dark = !$dark;
	};

	function setCookie(cname: string, cvalue: boolean, exdays: number) {
		const d = new Date();
		d.setTime(d.getTime() + exdays * 24 * 60 * 60 * 1000);
		let expires = 'expires=' + d.toUTCString();
		document.cookie = cname + '=' + cvalue + ';' + expires + ';path=/';
	}

	function getCookie(cname: string) {
		let name = cname + '=';
		let decodedCookie = decodeURIComponent(document.cookie);
		let ca = decodedCookie.split(';');
		for (let i = 0; i < ca.length; i++) {
			let c = ca[i];
			while (c.charAt(0) == ' ') {
				c = c.substring(1);
			}
			if (c.indexOf(name) == 0) {
				return c.substring(name.length, c.length);
			}
		}
		return '';
	}
</script>

<Column minwidth="100%" minheight="100vh" gap="10px" dark={$dark}>
	<div style="min-width: 100%;" class="mobile-hide">
		<Row
			gap="15px"
			alignitems="center"
			padding="10px 20px 10px 20px"
			minwidth="calc(100% - 40px)"
			justifycontent="end"
			dark={$dark}
		>
			<ButtonPrimary
				on:click={() => {
					aboutDialog = !aboutDialog;
				}}>About</ButtonPrimary
			>
			<ButtonPrimary>Projects</ButtonPrimary>
			<ButtonPrimary>Contact</ButtonPrimary>
			{#if $dark}
				<Row
					on:click={toggleDark}
					alignitems="center"
					minwidth="fit-content"
					cursor="pointer"
					grow="0"
					dark={$dark}
				>
					<Icon color="var(--darktext)" icon="fa-sun-bright" size="fa-xl" />
				</Row>
			{:else}
				<Row
					on:click={toggleDark}
					alignitems="center"
					minwidth="fit-content"
					cursor="pointer"
					grow="0"
					dark={$dark}
				>
					<Icon color="var(--primary)" icon="fa-moon" size="fa-xl" />
				</Row>
			{/if}
		</Row>
	</div>

	<div style="min-width: 100%;" class="mobile-show">
		<Row
			gap="25px"
			alignitems="center"
			padding="10px 20px 10px 20px"
			minwidth="calc(100% - 40px)"
			justifycontent="end"
			dark={$dark}
			minheight="calc(70px - 20px)"
		>
			<div style="min-height: 35px; display: flex; align-items: center; justify-content: center;">
				<input id="toggle-hamburger" type="checkbox" />
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
				<label
					class="hamburger-container"
					for="toggle-hamburger"
					on:click={() => {
						menuToggle = !menuToggle;
					}}
				>
					<div
						style="background-color: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; transition: all 150ms;"
						class="hamburger {$dark ? 'dark-hamburger' : 'light-hamburger'}"
					/>
				</label>
			</div>
			{#if $dark}
				<Row
					on:click={toggleDark}
					alignitems="center"
					minwidth="fit-content"
					cursor="pointer"
					grow="0"
					dark={$dark}
				>
					<Icon color="var(--darktext)" icon="fa-sun-bright" size="fa-xl" />
				</Row>
			{:else}
				<Row
					on:click={toggleDark}
					alignitems="center"
					minwidth="fit-content"
					cursor="pointer"
					grow="0"
					dark={$dark}
				>
					<Icon color="var(--primary)" icon="fa-moon" size="fa-xl" />
				</Row>
			{/if}
		</Row>
	</div>

	<div
		style="z-index: 10; position: absolute; top: 80px; border-radius: 5px; background: transparent; box-shadow: rgba(0,0,0,0.5) 0 5px 5px 0; min-width: calc(100% - 40px); transform: {menuToggle
			? 'scale(1)'
			: 'scale(0)'}; transition: all 150ms; overflow: hidden; margin: 0 20px 0 20px"
		class="mobile-show"
	>
		<Column background="var(--primary)" borderradius="5px">
			<Row
				alignitems="center"
				justifycontent="center"
				minwidth="100%"
				borderradius="5px"
				minheight="40px"
				margin="10px 0 0 0"
				cursor="pointer"
				background="var(--primary)"><P color="var(--darktext)">About</P></Row
			>
			<Row
				alignitems="center"
				justifycontent="center"
				minwidth="100%"
				borderradius="5px"
				minheight="40px"
				cursor="pointer"
				background="var(--primary)"><P color="var(--darktext)">Projects</P></Row
			>
			<Row
				alignitems="center"
				justifycontent="center"
				minwidth="100%"
				borderradius="5px"
				minheight="40px"
				margin="0 0 10px 0"
				cursor="pointer"
				background="var(--primary)"><P color="var(--darktext)">Contact</P></Row
			>
		</Column>
	</div>

	<slot />

	<Row
		grow="0"
		padding="0 20px 0 20px"
		margin="0 0 0 0"
		alignitems="center"
		justifycontent="end"
		minwidth="calc(100% - 40px)"
		dark={$dark}
	>
		<Column minwidth="100%" dark={$dark}>
			<div
				style="background: {$dark
					? 'var(--darktext)'
					: 'var(--primary)'}; height: 1px; width: 100%;"
			/>

			<Row margin="6px 0 0 0" minwidth="100%" dark={$dark}>
				<Row padding="0 50px" dark={$dark}>
					<div
						style="background: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; height: 1px; width: 20px; transform: rotate(-45deg);"
					/>
				</Row>
				<Row padding="0 50px" justifycontent="end" dark={$dark}>
					<div
						style="background: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; height: 1px; width: 20px; transform: rotate(45deg);"
					/>
				</Row>
			</Row>

			<Row margin="6px 0 0 0" minwidth="100%" dark={$dark}>
				<Row padding="0 25px" dark={$dark}>
					<div
						style="background: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; height: 1px; width: 25vw;"
					/>
				</Row>
				<Row padding="0 25px" justifycontent="end" dark={$dark}>
					<div
						style="background: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; height: 1px; width: 25vw;"
					/>
				</Row>
			</Row>
		</Column>
	</Row>

	<Row
		grow="0"
		alignitems="center"
		margin="15px 0 0 0"
		justifycontent="center"
		gap="20px"
		wrap="wrap"
		minwidth="100%"
		dark={$dark}
	>
		<Column alignitems="center" dark={$dark}>
			<Row justifycontent="center" padding="0 0 20px 0" dark={$dark}>
				<!-- svelte-ignore a11y-missing-attribute -->
				<P fontsize="12px" color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					>© 2022-2024 Development by Dalton Blake</P
				>
			</Row>
		</Column>
	</Row>
</Column>

<Dialog
	dark={$dark}
	display={aboutDialog}
	background={$dark ? 'rgb(40,40,40)' : 'white'}
>
	<Row
		background={$dark ? 'rgb(40,40,40)' : 'white'}
		alignitems="center"
		justifycontent="center"
		minwidth="200px"
		minheight="100px"
	>
		<P color={$dark ? 'var(--darktext)' : 'var(--primary)'}>Working on it</P>
	</Row>
</Dialog>

<style>
	#toggle-hamburger {
		display: none;
	}

	.hamburger-container {
		min-height: 35px;
		height: 35px;
		max-height: 35px;

		min-width: 35px;
		width: 35px;
		max-width: 35px;

		position: relative;

		display: flex;
		align-items: center;
		justify-content: center;

		cursor: pointer;
	}

	.hamburger {
		min-width: 35px;
		width: 35px;
		max-width: 35px;

		min-height: 2px;
		height: 2px;
		max-height: 2px;

		border-radius: 5px;

		transition: all 150ms;
	}

	.hamburger::before {
		min-width: 35px;
		width: 35px;
		max-width: 35px;

		min-height: 2px;
		height: 2px;
		max-height: 2px;

		border-radius: 5px;

		transition: all 150ms;

		position: absolute;
		top: 10px;
		content: '';
	}

	.hamburger::after {
		min-width: 35px;
		width: 35px;
		max-width: 35px;

		min-height: 2px;
		height: 2px;
		max-height: 2px;

		border-radius: 5px;

		transition: all 150ms;

		position: absolute;
		bottom: 10px;
		content: '';
	}

	.hamburger-container .light-hamburger::before {
		background: var(--primary) !important;
	}

	.hamburger-container .light-hamburger::after {
		background: var(--primary) !important;
	}

	.hamburger-container .dark-hamburger::before {
		background: var(--darktext) !important;
	}

	.hamburger-container .dark-hamburger::after {
		background: var(--darktext) !important;
	}

	#toggle-hamburger:checked + .hamburger-container .light-hamburger::before {
		transform: rotate(-45deg) translate(-5px, 5px);
		background: var(--primary) !important;
	}

	#toggle-hamburger:checked + .hamburger-container .light-hamburger::after {
		transform: rotate(45deg) translate(-4px, -4px);
		background: var(--primary) !important;
	}

	#toggle-hamburger:checked + .hamburger-container .dark-hamburger::before {
		transform: rotate(-45deg) translate(-5px, 5px);
		background: var(--darktext) !important;
	}

	#toggle-hamburger:checked + .hamburger-container .dark-hamburger::after {
		transform: rotate(45deg) translate(-4px, -4px);
		background: var(--darktext) !important;
	}

	#toggle-hamburger:checked + .hamburger-container .hamburger {
		background: transparent !important;
	}
</style>
