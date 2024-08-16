<script lang="ts">
	import Button from '$lib/Button.svelte';
	import Column from '$lib/Column.svelte';
	import Icon from '$lib/Icon.svelte';
	import Image from '$lib/Image.svelte';
	import Row from '$lib/Row.svelte';
	import Body from '$lib/Text/Body.svelte';
	import Card from '$lib/v2/Containers/cardtwo.svelte';
	import { text } from '@sveltejs/kit';

	import { dark } from '../ui_store';
	import Header from '$lib/Text/Header.svelte';
	import ButtonPrimary from '$lib/v2/Buttons/button-primary.svelte';
	import ButtonHover from '$lib/v2/Buttons/button-hover.svelte';
	import Cardtwo from '$lib/v2/Containers/cardtwo.svelte';

    var buttonsActive = false
    var containersActive = false
    var graphicsActive = false
    var inputsActive = false
    var shapesActive = false
    var textActive = false

	const toggleDark = async () => {
		$dark = !$dark;
	};

	const toggleHome = async () => {
		window.location.href = '/';
	};

    const resetMenu = async () => {
		buttonsActive = false
        containersActive = false
        graphicsActive = false
        inputsActive = false
        shapesActive = false
        textActive = false
	};
</script>

<Column
	background={$dark ? 'rgb(20,20,20)' : 'rgb(250,250,250)'}
	grow="1"
	minheight="100vh"
	padding="0 20px"
    overflowx="hidden"
>
	<Row align="center" height="100px" gap="20px" width="100%" zindex="2">
		<Row on:click={toggleHome} cursor="pointer" borderradius="5px">
			<!-- <Image src={Main_Logo} height="75px" width="150px" borderradius="5px" alt="Ktomek Logo" /> -->
		</Row>
		<div class="tablet-above">
			<Row gap="20px">
				<!-- <Button color="{$dark ? 'var(--darktext)' : 'var(--primary)'}"><a href="/auth?type=life" class="link-a">Life</a></Button> -->
				<!-- <Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><a href="/auth?type=work" class="link-a">About</a></Button
				> -->
			</Row>

			<Row marginleft="auto" gap="20px" align="center">
                <Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><a href="/#about" class="link-a">About</a></Button
				>
				<Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><a href="/#projects" class="link-a">Projects</a></Button
				>
				<Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><a href="/#blog" class="link-a">Blog</a></Button
				>
				<Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><a href="/#contact" class="link-a">Contact</a></Button
				>
				{#if $dark}
					<Row
						on:click={toggleDark}
						id="ui_mode"
						marginleft="auto"
						align="center"
						justify="center"
						padding="0 20px"
						cursor="pointer"
					>
						<Icon color="var(--darktext)" icon="fa-sun-bright" size="fa-xl" />
					</Row>
				{:else}
					<Row
						on:click={toggleDark}
						id="ui_mode"
						marginleft="auto"
						align="center"
						justify="center"
						padding="0 20px"
						cursor="pointer"
					>
						<Icon color="var(--primary)" icon="fa-moon" size="fa-xl" />
					</Row>
				{/if}
			</Row>
		</div>
		<div class="mobile-only" style="display: flex; align-items: center; gap: 10px; margin-right: 20px;">
			{#if $dark}
				<Row
					on:click={toggleDark}
					id="ui_mode"
					marginleft="auto"
					align="center"
					justify="center"
					padding="0 20px"
					cursor="pointer"
				>
					<Icon color="var(--darktext)" icon="fa-sun-bright" size="fa-xl" />
				</Row>
			{:else}
				<Row
					on:click={toggleDark}
					id="ui_mode"
					marginleft="auto"
					align="center"
					justify="center"
					padding="0 20px"
					cursor="pointer"
				>
					<Icon color="var(--primary)" icon="fa-moon" size="fa-xl" />
				</Row>
			{/if}

			<input id="menu-toggle" type="checkbox" />
			<label class="menu-button-container" for="menu-toggle">
				<div
					style="background-color: {$dark ? 'var(--darktext)' : 'var(--primary)'}"
					class="menu-button {$dark ? 'dark-menu' : 'light-menu'}"
				/>
			</label>

			<ul class="menu" style="background: {$dark ? 'rgb(20,20,20)' : 'rgb(250,250,250)'}">
				<li>
					<a
						href="/"
						class="link-a"
						style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Home</a
					>
				</li>
				<li>
					<a
						href="/#about"
						class="link-a"
						style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">About</a
					>
				</li>
				<li>
					<a
						href="/#projects"
						class="link-a"
						style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Projects</a
					>
				</li>
				<li>
					<a
						href="/#blog"
						class="link-a"
						style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Blog</a
					>
				</li>
				<!-- <li><a href="/auth?type=life" class="link-a" style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Ktomek Life</a></li> -->
				<li>
					<a
						href="/#contact"
						class="link-a"
						style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'} !important">Contact</a
					>
				</li>
			</ul>
		</div>
	</Row>

    <Column borderradius="5px" background="var(--primary)" align="center" width="100%" zindex="1" padding="0 0 10px 0">
        <Body height="0px" align="center" size="24px" color={$dark ? 'var(--darktext)' : 'var(--darktext)'}
            ><Icon icon="fa-code" size="fa-lg" color={$dark ? 'var(--darktext)' : 'var(--darktext)'}></Icon>&nbsp;&nbsp;UI Library</Body
        >
        <Body align="center" size="18px" color={$dark ? 'var(--darktext)' : 'var(--darktext)'}>UI component library for SvelteKit.</Body>
    </Column>

    <Row margintop="50px" gap="10px">
        <Row>
            <Button on:click={() => { resetMenu(); buttonsActive = true }} active={buttonsActive} color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><Icon icon="fa-square-check"></Icon>Buttons</Button
				>
        </Row>

        <Row>
            <Button on:click={() => { resetMenu(); containersActive = true }} active={containersActive} color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><Icon icon="fa-container-storage"></Icon>Containers</Button>
        </Row>

        <Row>
            <Button on:click={() => { resetMenu(); graphicsActive = true }} active={graphicsActive} color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><Icon icon="fa-image"></Icon>Graphics</Button>
        </Row>

        <Row>
            <Button on:click={() => { resetMenu(); inputsActive = true }} active={inputsActive} color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><Icon icon="fa-input-pipe"></Icon>Inputs</Button>
        </Row>

        <Row>
            <Button on:click={() => { resetMenu(); shapesActive = true }} active={shapesActive} color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><Icon icon="fa-shapes"></Icon>Shapes</Button>
        </Row>

        <Row>
            <Button on:click={() => { resetMenu(); textActive = true }} active={textActive} color={$dark ? 'var(--darktext)' : 'var(--primary)'}
					><Icon icon="fa-text"></Icon>Text</Button>
        </Row>
    </Row>

    <Column minheight="25vh" margintop="50px" width="calc(100% - 100px)" padding="0 50px">
        {#if buttonsActive}
			<Row gap="25px" wrap="wrap">
				<Button color={$dark ? 'var(--darktext)' : 'var(--primary)'}>Link Button</Button>
				<Button color={$dark ? 'var(--darktext)' : 'var(--primary)'} buttonType="success">Success Button</Button>
				<Button color={$dark ? 'var(--darktext)' : 'var(--primary)'} buttonType="warn">Warn Button</Button>
				<ButtonPrimary>Solid Button</ButtonPrimary>
				{#if !$dark} 
					<ButtonHover>Hover Button</ButtonHover>
				{/if}
			</Row>
		{:else if containersActive}
			<Column gap="10px">
				<Header color="{$dark ? 'var(--darktext)' : 'var(--primary)'}">Card</Header>
				<Column gap="10px" padding="15px">
					<Cardtwo dark="{$dark}" padding="10px 20px">
						<Column>
							<Body weight="500" size="18px" color="{$dark ? 'var(--darktext)' : 'var(--primary)'}">Welcome to my UI Portfolio</Body>
							<Body color="{$dark ? 'var(--darktext)' : 'var(--primary)'}">Here you can find a variety of coding projects I am working on.</Body>
						</Column>					
					</Cardtwo>
					<Body color="{$dark ? 'var(--darktext)' : 'var(--primary)'}">Here is the HTML for the Card component:</Body>
					<code style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'}">
						&lt;div on:click style="<br>
						&nbsp;&nbsp;&nbsp;&nbsp;display: {`{display}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;flex-direction: {`{direction}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;align-items: {`{alignitems}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;align-content: {`{aligncontent}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;align-self: {`{alignself}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;justify-items: {`{justifyitems}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;justify-content: {`{justifycontent}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;justify-self: {`{justifyself}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;gap: {`{gap}`};<br>
						<br>
						&nbsp;&nbsp;&nbsp;&nbsp;height: {`{height}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;min-height: {`{minheight}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;max-height: {`{maxheight}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;width: {`{width}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;min-width: {`{minwidth}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;max-width: {`{maxwidth}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;flex-grow: {`{grow}`};<br>
						<br>
						&nbsp;&nbsp;&nbsp;&nbsp;padding: {`{padding}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;margin: {`{margin}`};<br>
						<br>
						&nbsp;&nbsp;&nbsp;&nbsp;background: {`{dark ? 'rgb(40,40,40)' : background}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;border: {`{border}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;border-radius: {`{borderradius}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;box-shadow: {`{boxshadow}`}; <br>
						&nbsp;&nbsp;&nbsp;&nbsp;cursor: {`{cursor}`};<br>
						<br>
						&nbsp;&nbsp;&nbsp;&nbsp;overflow-x: {`{overflowx}`};<br>
						&nbsp;&nbsp;&nbsp;&nbsp;overflow-y: {`{overflowy}`};<br>
						<br>
						&nbsp;&nbsp;&nbsp;&nbsp;position: {`{position}`};<br>
						<br>
						&nbsp;&nbsp;&nbsp;&nbsp;transition: {`{transition}`};<br>
						"&gt;<br>
						&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;slot /&gt;<br>
						&lt;/div&gt;
					</code>
					<Body color="{$dark ? 'var(--darktext)' : 'var(--primary)'}">Here are the parameters for the Card component:</Body>
					<code style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'}">
						export let dark = false;<br>
						<br>
						export let display = "flex";<br>
						export let direction = "row";<br>
						export let alignitems = "normal";<br>
						export let aligncontent = "stretch";<br>
						export let alignself = "auto";<br>
						export let justifyitems = "normal";<br>
						export let justifycontent = "stretch";<br>
						export let justifyself = "auto";<br>
						export let gap = "0";<br>
						<br>
						export let height = "fit-content";<br>
						export let minheight = "50px";<br>
						export let maxheight = "fit-content";<br>
						export let width = "fit-content";<br>
						export let minwidth = "50px";<br>
						export let maxwidth = "fit-content";<br>
						export let grow = "0";<br>
						<br>
						export let padding = "0 0 0 0";<br>
						export let margin = "0 0 0 0";<br>
						<br>
						export let background = "white";<br>
						export let border = "none";<br>
						export let borderradius = "5px";<br>
						export let boxshadow = "rgba(50, 50, 93, 0.25) 0px 13px 27px -5px, rgba(0, 0, 0, 0.3) 0px 8px 16px -8px";<br>
						export let cursor = "default";<br>
						<br>
						export let overflowx = "hidden";<br>
						export let overflowy = "hidden";<br>
						<br>
						export let position = "relative";<br>
						<br>
						export let transition = "all 300ms";<br>
					</code>
					<Body color="{$dark ? 'var(--darktext)' : 'var(--primary)'}">Here is an example usage of the Card component:</Body>
					<code style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'}">
						&lt;Card dark={'{$dark}'} minheight="150px" minwidth="150px"&gt; -- content --  &lt;/Card&gt;
					</code>
					<Body color="{$dark ? 'var(--darktext)' : 'var(--primary)'}">Which then produces this:</Body>
					<Cardtwo dark={$dark} minheight="150px" minwidth="150px"></Cardtwo>
				</Column>
			</Column>
		{:else if graphicsActive}

		{:else if inputsActive}

		{:else if shapesActive}

		{:else if textActive}

		{/if}
    </Column>

	<Row margintop="25px" width="100%" height="100%" align="center" justify="end">
		<Column width="100%">
			<div
				style="background: {$dark
					? 'var(--darktext)'
					: 'var(--primary)'}; height: 1px; width: 100%;"
			/>

			<Row width="100%" margintop="6px">
				<Row padding="0 50px">
					<div
						style="background: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; height: 1px; width: 20px; transform: rotate(-45deg);"
					/>
				</Row>
				<Row padding="0 50px" marginleft="auto">
					<div
						style="background: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; height: 1px; width: 20px; transform: rotate(45deg);"
					/>
				</Row>
			</Row>

			<Row width="100%" margintop="6px">
				<Row padding="0 25px">
					<div
						style="background: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; height: 1px; width: 25vw;"
					/>
				</Row>
				<Row padding="0 25px" marginleft="auto">
					<div
						style="background: {$dark
							? 'var(--darktext)'
							: 'var(--primary)'}; height: 1px; width: 25vw;"
					/>
				</Row>
			</Row>
		</Column>
	</Row>

	<Row align="center" margintop="15px" justify="center" gap="20px" width="100%" wrap="wrap">
		<Column align="center">
			<Row justify="center" padding="0 0 20px 0">
				<!-- svelte-ignore a11y-missing-attribute -->
				<Body color={$dark ? 'var(--darktext)' : 'var(--primary)'}>© 2022-2024 Development by Dalton Blake</Body>
			</Row>
		</Column>
	</Row>
</Column>

<style>
	code {
		background: rgba(0,0,0,0.1);
		padding: 15px;
		border-radius: 5px;
	}
</style>