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
	import Image from '$lib/Graphics/Image.svelte';
	import H2 from '$lib/Text/H2.svelte';
	import Textbox from '$lib/Inputs/textbox.svelte';

	let menuToggle: boolean = false;
	let aboutDialog: boolean = false;
	let projectsDialog: boolean = false;

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
					window.location.href = '/';
				}}>Home</ButtonPrimary
			>
			<ButtonPrimary
				on:click={() => {
					aboutDialog = !aboutDialog;
				}}>About</ButtonPrimary
			>
			<ButtonPrimary
				on:click={() => {
					projectsDialog = !projectsDialog;
				}}>Projects</ButtonPrimary
			>
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
				background="var(--primary)"
				on:click={() => {
					window.location.href = '/';
				}}><P color="var(--darktext)">Home</P></Row
			>
			<Row
				alignitems="center"
				justifycontent="center"
				minwidth="100%"
				borderradius="5px"
				minheight="40px"
				margin="0 0 0 0"
				cursor="pointer"
				background="var(--primary)"
				on:click={() => {
					aboutDialog = !aboutDialog;
				}}><P color="var(--darktext)">About</P></Row
			>
			<Row
				alignitems="center"
				justifycontent="center"
				minwidth="100%"
				borderradius="5px"
				minheight="40px"
				padding="0 0 10px 0"
				cursor="pointer"
				background="var(--primary)"
				on:click={() => {
					projectsDialog = !projectsDialog;
				}}><P color="var(--darktext)">Projects</P></Row
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
	overflow="auto"
>
	<Row background={$dark ? 'rgb(40,40,40)' : 'white'} padding="20px 20px 0 20px" gap="15px">
		<Image
			src="/Dalton_Blake_Professional_Photo.jpg"
			maxheight="125px"
			maxwidth="125px"
			borderradius="5px"
		></Image>
		<div class="mobile-hide">
			<Column
				background={$dark ? 'rgb(40,40,40)' : 'white'}
				justifycontent="center"
				padding="10px 20px"
			>
				<H2 color={$dark ? 'var(--darktext)' : 'var(--primary)'}>Dalton Blake</H2>
				<Row background={$dark ? 'rgb(40,40,40)' : 'white'} gap="15px">
					<Row
						cursor="pointer"
						on:click={() => {
							window.location.href = 'https://bcert.me/sqalzkqmt';
						}}
						background={$dark ? 'rgb(40,40,40)' : 'white'}
					>
						<Image src="/CAL_1_Badge.png" maxheight="50px" maxwidth="50px" borderradius="5px"
						></Image>
					</Row>
					<Row
						cursor="pointer"
						on:click={() => {
							window.location.href = 'https://bcert.me/sendfcmxe';
						}}
						background={$dark ? 'rgb(40,40,40)' : 'white'}
					>
						<Image src="/CSD_Badge.png" maxheight="50px" maxwidth="50px" borderradius="5px"></Image>
					</Row>
				</Row>
			</Column>
		</div>

		<Row
			on:click={() => {
				aboutDialog = !aboutDialog;
			}}
			background={$dark ? 'rgb(40,40,40)' : 'white'}
			justifycontent="end"
		>
			<ButtonPrimary>Close</ButtonPrimary>
		</Row>
	</Row>

	<div class="mobile-show">
		<Row
			background={$dark ? 'rgb(40,40,40)' : 'white'}
			padding="0 20px"
			alignitems="center"
			gap="15px"
		>
			<H2 color={$dark ? 'var(--darktext)' : 'var(--primary)'}>Dalton Blake</H2>
			<Row background={$dark ? 'rgb(40,40,40)' : 'white'} gap="15px">
				<Row
					grow="0"
					cursor="pointer"
					on:click={() => {
						window.location.href = 'https://bcert.me/sqalzkqmt';
					}}
					background={$dark ? 'rgb(40,40,40)' : 'white'}
				>
					<Image src="/CAL_1_Badge.png" maxheight="50px" maxwidth="50px" borderradius="5px"></Image>
				</Row>
				<Row
					grow="0"
					cursor="pointer"
					on:click={() => {
						window.location.href = 'https://bcert.me/sendfcmxe';
					}}
					background={$dark ? 'rgb(40,40,40)' : 'white'}
				>
					<Image src="/CSD_Badge.png" maxheight="50px" maxwidth="50px" borderradius="5px"></Image>
				</Row>
			</Row>
		</Row>
	</div>

	<Row
		background={$dark ? 'rgb(40,40,40)' : 'white'}
		margin="0 0 0 0"
		padding="0 20px 0 20px"
		maxwidth="750px"
	>
		<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} textalign="justify"
			>Technically minded and detail-oriented professional with dynamic experience in designing and
			executing innovative software solutions. Proficient in utilizing C#, TypeScript, SQL, and
			PostgreSQL, managing SEO, implementing custom application features, and UI/UX design.</P
		>
	</Row>

	<Row
		background={$dark ? 'rgb(40,40,40)' : 'white'}
		padding="0 20px 20px 20px"
		gap="15px"
		wrap="wrap"
	>
		<Column
			grow="1"
			minwidth="275px"
			background="var(--primary)"
			borderradius="5px"
			overflowx="hidden"
			overflowy="hidden"
			padding="15px"
			gap="15px"
		>
			<Row background="var(--primary)" padding="0 10px" minwidth="calc(100% - 20px)">
				<P fontweight="600" color="var(--darktext)" textalign="center"
					>4.33 Years Professional Experience</P
				>
			</Row>
			<div style="background: var(--darktext); min-height: 1px; min-width: 100%;"></div>
			<Column background="var(--primary)" gap="5px" padding="0 10px">
				<P color="var(--darktext)"
					>Software Engineer: <span style="font-weight: 600;">&nbsp;&nbsp;2 Years</span></P
				>
				<P color="var(--darktext)"
					>Software Developer: <span style="font-weight: 600;">&nbsp;&nbsp;2 Years</span></P
				>
				<P color="var(--darktext)"
					>Data Quality: <span style="font-weight: 600;">&nbsp;&nbsp;4 Months</span></P
				>
			</Column>
		</Column>

		<Column
			minwidth="275px"
			background="var(--primary)"
			borderradius="5px"
			overflowx="hidden"
			overflowy="hidden"
			padding="15px"
			gap="15px"
		>
			<Row background="var(--primary)" padding="0 10px" minwidth="calc(100% - 20px)">
				<P fontweight="600" color="var(--darktext)" textalign="center">6 Certifications</P>
			</Row>
			<div style="background: var(--darktext); min-height: 1px; min-width: 100%;"></div>
			<Column background="var(--primary)" gap="5px" padding="0 10px">
				<P color="var(--darktext)">Certified Agile Leader® 1</P>
				<P color="var(--darktext)">Certified Scrum Developer®</P>
				<P color="var(--darktext)">Relational Database</P>
				<P color="var(--darktext)">Foundational C# with Microsoft</P>
				<P color="var(--darktext)">JavaScript Algorithms & Data Structures (Beta)</P>
				<P color="var(--darktext)">Responsive Web Design</P>
			</Column>
		</Column>
	</Row>
</Dialog>

<Dialog dark={$dark} display={projectsDialog} background={$dark ? 'rgb(40,40,40)' : 'white'}>
	<Row background={$dark ? 'rgb(40,40,40)' : 'white'} padding="20px 20px 0 20px" gap="25px">
		<div style="max-width: 750px !important; width: 100vw;">
			<Textbox
				dark={$dark}
				id="searchProject"
				name="searchProject"
				placeholder="Search for a project"
			></Textbox>
		</div>
		<Row
			grow="0"
			on:click={() => {
				projectsDialog = !projectsDialog;
			}}
			background={$dark ? 'rgb(40,40,40)' : 'white'}
			justifycontent="end"
		>
			<ButtonPrimary>Close</ButtonPrimary>
		</Row>
	</Row>

	<Row background={$dark ? 'rgb(40,40,40)' : 'white'} padding="0 20px 20px 20px">
		<Column
			maxwidth="fit-content"
			background={$dark ? 'rgb(40,40,40)' : 'white'}
			borderradius="5px"
			border="solid 2px var(--primary)"
			overflowx="hidden"
			overflowy="hidden"
			gap="10px"
			cursor="pointer"
			on:click={() => {
				window.location.href = '/ui-components';
			}}
		>
			<Row background={$dark ? 'rgb(40,40,40)' : 'white'} minwidth="100%" cursor="pointer">
				<Image src="/UI_Components.png" maxheight="100px"></Image>
			</Row>
			<Row background={$dark ? 'rgb(40,40,40)' : 'white'} padding="0 10px" cursor="pointer">
				<P
					color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					fontsize="18px"
					textdecoration="underline">UI Components</P
				>
			</Row>
			<Row
				background={$dark ? 'rgb(40,40,40)' : 'white'}
				padding="0 10px 10px 10px"
				cursor="pointer"
			>
				<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontsize="14px"
					>A set of UI Components for SvelteKit.</P
				>
			</Row>
			<Row
				background={$dark ? 'rgb(40,40,40)' : 'white'}
				padding="0 10px 10px 10px"
				cursor="pointer"
				gap="10px"
			>
				<Row background="var(--primary)" padding="5px" borderradius="5px">
					<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} fontsize="12px">SvelteKit</P>
				</Row>
				<Row background="var(--primary)" padding="5px" borderradius="5px">
					<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} fontsize="12px">HTML</P>
				</Row>
				<Row background="var(--primary)" padding="5px" borderradius="5px">
					<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} fontsize="12px">CSS</P>
				</Row>
				<Row background="var(--primary)" padding="5px" borderradius="5px">
					<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} fontsize="12px">UI</P>
				</Row>
			</Row>
		</Column>
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
