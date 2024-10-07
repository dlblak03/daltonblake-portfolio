<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import Row from '$lib/Containers/Row.svelte';
	import Icon from '$lib/Graphics/Icon.svelte';

	import H3 from '$lib/Text/H3.svelte';
	import P from '$lib/Text/P.svelte';

	import { dark } from './ui_store';
</script>

<svelte:head>
	<title>Dalton Blake</title>

	<meta
		name="description"
		content="Technically minded and detail-oriented professional with dynamic experience in designing and executing innovative software solutions.
        Adept at providing strategic guidance to clients to optimise application usability and functionality."
	/>
</svelte:head>

<Column justifycontent="center" alignitems="center" minwidth="100%" dark={$dark}>
	<Row grow="0" margin="0 0 10px 0" dark={$dark} justifycontent="center" alignitems='center'>
		<P fontsize="14px" color={$dark ? 'var(--darktext)' : 'var(--primary)'} letterspacing="0.25rem" textalign='center'>EXPERIENCE</P>
	</Row>
	<Row grow="0" dark={$dark} justifycontent="center" alignitems='center'>
		<H3 color={$dark ? 'var(--darktext)' : 'var(--primary)'} letterspacing="0.25rem" textalign='center'>LIFE WITH DALTON</H3>
	</Row>
	<Row grow="0" dark={$dark} justifycontent="center" alignitems='center'>
		<P fontsize="14px" color={$dark ? 'var(--darktext)' : 'var(--primary)'} letterspacing="0.25rem" textalign='center'>INNOVATIVE, TRANSFORMATIVE CHANGE</P>
	</Row>

	<div class="mobile-show-animate" style="margin-top: 50px; box-shadow: rgba(0,0,0,0.5) 0 5px 5px 0; display: flex; align-items: center; width: 125px; height: 35px; gap: 10px; background: var(--primary); padding: 15px 20px; border-radius: 5px;">
		<Row cursor="pointer" on:click={() => {window.location.href="https://www.linkedin.com/in/daltonblake05/"}} background="transparent" alignitems="center" justifycontent="center">
			<Icon color="{$dark ? 'var(--darktext)' : 'var(--darktext)'}" icon="fa-brands fa-linkedin" size="fa-xl"></Icon>
		</Row>
		<Row cursor="pointer" on:click={() => {window.location.href="https://github.com/dlblak03"}} background="transparent" alignitems="center" justifycontent="center">
			<Icon color="{$dark ? 'var(--darktext)' : 'var(--darktext)'}" icon="fa-brands fa-github" size="fa-xl"></Icon>
		</Row>
		<Row cursor="pointer" on:click={() => {window.location.href="https://codepen.io/dlblak03"}} background="transparent" alignitems="center" justifycontent="center">
			<Icon color="{$dark ? 'var(--darktext)' : 'var(--darktext)'}" icon="fa-brands fa-codepen" size="fa-xl"></Icon>
		</Row>
	</div>
</Column>

<div class="mobile-hide-animate" style="box-shadow: rgba(0,0,0,0.5) 0 5px 5px 0; position: absolute; left: 20px; top: calc(50% - 125px); display: flex; flex-direction: column; height: 125px; gap: 10px; background: var(--primary); padding: 15px 20px; border-radius: 5px;">
	<Row cursor="pointer" on:click={() => {window.location.href="https://www.linkedin.com/in/daltonblake05/"}} background="transparent" alignitems="center" justifycontent="center">
		<Icon color="{$dark ? 'var(--darktext)' : 'var(--darktext)'}" icon="fa-brands fa-linkedin" size="fa-xl"></Icon>
	</Row>
	<Row cursor="pointer" on:click={() => {window.location.href="https://github.com/dlblak03"}} background="transparent" alignitems="center" justifycontent="center">
		<Icon color="{$dark ? 'var(--darktext)' : 'var(--darktext)'}" icon="fa-brands fa-github" size="fa-xl"></Icon>
	</Row>
	<Row cursor="pointer" on:click={() => {window.location.href="https://codepen.io/dlblak03"}} background="transparent" alignitems="center" justifycontent="center">
		<Icon color="{$dark ? 'var(--darktext)' : 'var(--darktext)'}" icon="fa-brands fa-codepen" size="fa-xl"></Icon>
	</Row>
</div>
