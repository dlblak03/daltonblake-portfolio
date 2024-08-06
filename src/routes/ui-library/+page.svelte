<script lang="ts">
	import Button from '$lib/Button.svelte';
	import Column from '$lib/Column.svelte';
	import Icon from '$lib/Icon.svelte';
	import Image from '$lib/Image.svelte';
	import Row from '$lib/Row.svelte';
	import Body from '$lib/Text/Body.svelte';
	import Card from '$lib/v2/Containers/card.svelte';

	import { dark } from '../ui_store';

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

    <Column>
        
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