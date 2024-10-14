<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import Row from '$lib/Containers/Row.svelte';
	import Icon from '$lib/Graphics/Icon.svelte';

	import H3 from '$lib/Text/H3.svelte';
	import P from '$lib/Text/P.svelte';

	import { dark } from '../ui_store';

	let menuToggleLeft: Number = 4;
	let selectedSection: String = 'Buttons';

	let selectedSubSection: String = 'Primary';
</script>

<svelte:head>
	<title>Dalton Blake | UI Components</title>

	<meta name="description" content="" />
</svelte:head>

<Column minwidth="100%" dark={$dark}>
	<Row
		background="transparent"
		grow="0"
		justifycontent="center"
		minwidth="100%"
		margin="25px 0 0 0"
	>
		<H3 color={$dark ? 'var(--darktext)' : 'var(--primary)'}>SvelteKit UI Components</H3>
	</Row>
	<Row background="transparent" grow="0" justifycontent="center" minwidth="100%">
		<P color={$dark ? 'var(--darktext)' : 'var(--primary)'}
			>This page displays the UI Components I've created using SvelteKit - an easy to use full-stack
			framework.</P
		>
	</Row>

	<Row
		grow="0"
		background="transparent"
		justifycontent="center"
		minwidth="100%"
		margin="25px 0 25px 0"
	>
		<Row
			justifycontent="center"
			maxwidth="fit-content"
			background="var(--primary)"
			borderradius="5px"
			gap="5px"
		>
			<div
				style="position: absolute; left: {menuToggleLeft}px; top: 4px; transition: all 150ms; height: calc(100% - 12px); border: solid 2px var(--darktext); width: 100px; border-radius: 5px;"
			></div>
			<Row
				on:click={() => {
					menuToggleLeft = 4;
					selectedSection = 'Buttons';
					selectedSubSection = 'Primary';
				}}
				background="transparent"
				justifycontent="center"
				cursor="pointer"
				padding="20px"
				minwidth="75px"
			>
				<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} textalign="center">Buttons</P>
			</Row>
			<Row
				on:click={() => {
					menuToggleLeft = 128;
					selectedSection = 'Containers';
					selectedSubSection = 'Card';
				}}
				background="transparent"
				justifycontent="center"
				cursor="pointer"
				padding="20px"
				minwidth="75px"
			>
				<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} textalign="center">Containers</P>
			</Row>
			<Row
				on:click={() => {
					menuToggleLeft = 249;
					selectedSection = 'Graphics';
                    selectedSubSection = "Icon"
				}}
				background="transparent"
				justifycontent="center"
				cursor="pointer"
				padding="20px"
				minwidth="75px"
			>
				<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} textalign="center">Graphics</P>
			</Row>
			<Row
				on:click={() => {
					menuToggleLeft = 369;
					selectedSection = 'Inputs';
				}}
				background="transparent"
				justifycontent="center"
				cursor="pointer"
				padding="20px"
				minwidth="75px"
			>
				<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} textalign="center">Inputs</P>
			</Row>
			<Row
				on:click={() => {
					menuToggleLeft = 489;
					selectedSection = 'Shapes';
				}}
				background="transparent"
				justifycontent="center"
				cursor="pointer"
				padding="20px"
				minwidth="75px"
			>
				<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} textalign="center">Shapes</P>
			</Row>
			<Row
				on:click={() => {
					menuToggleLeft = 610;
					selectedSection = 'Text';
				}}
				background="transparent"
				justifycontent="center"
				cursor="pointer"
				padding="20px"
				minwidth="75px"
			>
				<P color={$dark ? 'var(--darktext)' : 'var(--darktext)'} textalign="center">Text</P>
			</Row>
		</Row>
	</Row>

	{#if selectedSection == 'Buttons'}
		<Row background="transparent" justifycontent="center" minwidth="100%" margin="25px 0 0 0">
			<Column
				grow="0"
				background={$dark ? 'rgb(40,40,40)' : 'rgba(0,0,0,0.1)'}
				padding="5px"
				borderradius="5px"
				gap="2px"
			>
				<Row
					on:click={() => {
						selectedSubSection = 'Primary';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Primary'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Primary</P>
				</Row>
				<Row
					on:click={() => {
						selectedSubSection = 'Hover';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Hover'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Hover</P>
				</Row>
			</Column>
			<Row background="transparent" maxwidth="750px"></Row>
		</Row>
	{:else if selectedSection == 'Containers'}
		<Row background="transparent" justifycontent="center" minwidth="100%" margin="25px 0 0 0">
			<Column
				grow="0"
				background={$dark ? 'rgb(40,40,40)' : 'rgba(0,0,0,0.1)'}
				padding="5px"
				borderradius="5px"
				gap="2px"
			>
				<Row
					on:click={() => {
						selectedSubSection = 'Card';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Card'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Card</P>
				</Row>
				<Row
					on:click={() => {
						selectedSubSection = 'Column';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Column'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Column</P>
				</Row>
				<Row
					on:click={() => {
						selectedSubSection = 'Dialog';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Dialog'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Dialog</P>
				</Row>
				<Row
					on:click={() => {
						selectedSubSection = 'Row';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Row'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Row</P>
				</Row>
				<Row
					on:click={() => {
						selectedSubSection = 'Snackbar';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Snackbar'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Snackbar</P>
				</Row>
			</Column>
			<Row background="transparent" maxwidth="750px"></Row>
		</Row>
	{:else if selectedSection == 'Graphics'}
		<Row background="transparent" justifycontent="center" minwidth="100%" margin="25px 0 0 0">
			<Column
				grow="0"
				background={$dark ? 'rgb(40,40,40)' : 'rgba(0,0,0,0.1)'}
				padding="5px"
				borderradius="5px"
				gap="2px"
			>
				<Row
					on:click={() => {
						selectedSubSection = 'Icon';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Icon'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Icon</P>
				</Row>
				<Row
					on:click={() => {
						selectedSubSection = 'Image';
					}}
					cursor="pointer"
					background={selectedSubSection == 'Image'
						? $dark
							? 'rgb(250,250,250,0.1)'
							: 'rgba(0,0,0,0.1)'
						: 'transparent'}
					minwidth="100px"
					padding="10px 10px"
					borderradius="5px"
				>
					<P color={$dark ? 'var(--darktext)' : 'var(--primary)'} fontweight="500">Image</P>
				</Row>
			</Column>
			<Row background="transparent" maxwidth="750px"></Row>
		</Row>
	{/if}
</Column>
