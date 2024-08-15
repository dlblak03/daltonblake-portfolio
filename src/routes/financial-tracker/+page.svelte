<script lang="ts">
	import Column from '$lib/Column.svelte';
    import ColumnTwo from '$lib/v2/Containers/columntwo.svelte';
	import Row from '$lib/Row.svelte';

    import Card from '$lib/v2/Containers/cardtwo.svelte';
	import Body from '$lib/Text/Body.svelte';
	import Button from '$lib/Button.svelte';
	import Icon from '$lib/Icon.svelte';

	import { dark } from '../ui_store';

	import type { PageData } from './$types';
	import { onMount } from 'svelte';

	export let data: PageData;

    let daysInMonth: any = [];

	onMount(async () => {
		const today = new Date();
        const currentYear = today.getFullYear();
        const currentMonth = today.getMonth();
        daysInMonth = getDaysInMonth(currentYear, currentMonth);
	});

    const toggleDark = async () => {
		$dark = !$dark;
	};

	const toggleHome = async () => {
		window.location.href = '/';
	};

    function getDaysInMonth(year: any, month: any) {
    const date = new Date(year, month, 0);
    const days = [];
    for (let i = 1; i <= date.getDate(); i++) {
        days.push((new Date(year, month, i)).toLocaleDateString());
    }
    return days;
    }
</script>

<svelte:head>
	<title>Dalton Blake | Financial Tracker</title>

	<meta
		name="description"
		content=""
	/>
</svelte:head>

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
		><Icon icon="fa-piggy-bank" size="fa-lg" color={$dark ? 'var(--darktext)' : 'var(--darktext)'}></Icon>&nbsp;&nbsp;Financial Tracker</Body
	>
	<Body align="center" size="18px" color={$dark ? 'var(--darktext)' : 'var(--darktext)'}>UI for managing financial transactions.</Body>
</Column>

<Row width="100%" margintop="25px">
    <Card width="100%" maxwidth="100%" dark={$dark}>
        <ColumnTwo overflowx="auto">
            <Row minheight="175px" height="100%">
                <Row height="100%" background="var(--warn)" border="solid 1px var(--primary)" width="50px" align="center">
                    <div style="color: var(--darktext); width: 80%; writing-mode: vertical-rl; font-size: 24px;">
                        RECURRING
                    </div>
                </Row>
                <div style="display: flex; height: calc(100% - 1px); border: solid 1px var(--primary); border-left: none;" class="alternating-bg {$dark ? 'dark-bg' : ''}">
                    {#each daysInMonth as day}                    
                        <div>
                        
                        </div>                        
                    {/each}
                </div>
            </Row>
            <Row minheight="175px"  height="100%" >
                <Row height="100%" width="50px" background="var(--warn)" border="solid 1px var(--primary)" align="center">
                    <div style="color: var(--darktext); width: 80%; writing-mode: vertical-rl; font-size: 24px;">
                        SINGLE
                    </div>
                </Row>
                <div style="display: flex; height: calc(100% - 1px); border: solid 1px var(--primary); border-left: none;" class="alternating-bg {$dark ? 'dark-bg' : ''}">
                    {#each daysInMonth as day}                    
                        <div>
                        
                        </div>                        
                    {/each}
                </div>
            </Row>
            <Row minheight="25px" height="25px"  background="var(--primary)" width="100%">
                <div style="min-width: 50px; background: var(--primary); border-right: solid 1px var(--primary); border-left: solid 1px var(--primary)"></div>
                <div style="display: flex; height: calc(100% - 1px); border: solid 1px var(--primary); border-left: none; background: var(--primary)">
                    {#each daysInMonth as day}                    
                        <div style="display: flex; align-items: center; justify-content: center; min-width: 150px; max-width: 150px; border-right: solid 1px var(--primary)">
                            <p style="color: var(--darktext)">{day}</p>
                        </div>                        
                    {/each}
                </div>
            </Row>
            <Row minheight="175px">
                <Row height="calc(100% - 2px)" width="50px" background="var(--success)" border="solid 1px var(--primary)" align="center">
                    <div style="color: var(--darktext); width: 80%; writing-mode: vertical-rl; font-size: 24px;">
                        INCOME
                    </div>
                </Row>
                <div style="display: flex; height: calc(100% - 2px); border: solid 1px var(--primary); border-left: none;" class="alternating-bg {$dark ? 'dark-bg' : ''}">
                    {#each daysInMonth as day}                    
                        <div>
                        
                        </div>                        
                    {/each}
                </div>
            </Row>
        </ColumnTwo>
    </Card>
</Row>

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

<style type="text/css">
    .alternating-bg > div:nth-child(2n + 1) {
        min-width: 150px;
        max-width: 150px;
        background: rgb(240,240,240) !important;
        border-right: solid 1px var(--primary);
    }

    .dark-bg > div:nth-child(2n + 1) {
        background: rgb(40,40,40) !important;
    }

    .alternating-bg > div:nth-child(2n) {
        min-width: 150px;
        max-width: 150px;
        background: white !important;
        border-right: solid 1px var(--primary);
    }

    .dark-bg > div:nth-child(2n) {
        background: rgb(75,75,75) !important;
    }

    .alternating-bg > div:last-child {
        border-right: none;
    }
</style>