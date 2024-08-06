<script lang="ts">
	import Icon from './Icon.svelte';
	import Row from './Row.svelte';
	import Column from './Column.svelte';
	import Textbox from './Textbox.svelte';
	import type Dialog from './Dialog.svelte';

	export let dark = false;
	export let width = 'auto';
	export let cursor = 'default';

	export let data: any[] = [];
	let originalData: any[] | null = null;
	export let groups: any[] = [];

	export let columns: any[] = [];

	export let searchid = '';
	export let searchValue = '';

	export let whitelabel = false;
	export let primarycolor = '#540000';

	export let imageTileView: boolean = false;
	export let imageColumn: string = '';
	export let altColumn: string = '';
	export let imageBase: string = '';

	export let leadsView: boolean = false;

	export let rocketsView: boolean = false;
	export let rocketNameDialog: any = null;
	export let rocketDescriptionDialog: any = null;
	export let rocketChatDialog: any = null;
	export let selectedRocket: any = null;

	export let rowClick = async (dataRow: any) => {};

	const filterData = async () => {
		if (originalData == null) {
			originalData = data;
		}
		if (searchValue.length == 0) {
			data = originalData;
			return;
		}

		var results: any[] = [];

		for (var i = 0; i < originalData.length; i++) {
			let continueBool = false;
			for (var key in originalData[i]) {
				if (continueBool) {
					continue;
				}
				if (originalData[i][key].indexOf(searchValue) != -1) {
					results.push(JSON.parse(JSON.stringify(originalData[i])));
					continueBool = true;
				}
			}
		}
		data = results;
	};
</script>

<div
	style="display: flex; height: 100%; flex-direction: column; flex-grow: 1; gap: 10px; width: {width}"
>
	<div style="display: flex;">
		<Textbox
			{whitelabel}
			{primarycolor}
			{dark}
			bind:value={searchValue}
			id={searchid}
			on:keyup={() => {
				filterData();
			}}>Search data</Textbox
		>
	</div>

	<div style="display: flex; margin-top: 15px;">
		<slot />
	</div>

	<div
		class="ktomek-table-wrapper {dark ? 'ktomek-dark-table-wrapper' : ''}"
		style="display: flex; overflow-y: auto; overflow-x: visible; {rocketsView
			? 'justify-content: center;'
			: ''}"
	>
		{#if !imageTileView && !leadsView && !rocketsView}
			<table
				style="border-top: solid 2px {whitelabel
					? primarycolor
					: 'var(--primary)'}; border-bottom: solid 2px {whitelabel
					? primarycolor
					: 'var(--primary)'}; background: {whitelabel ? primarycolor : 'var(--primary)'}"
				class="ktomek-table {dark ? 'ktomek-dark-table' : ''}"
			>
				{#if groups.length == 0}
					<thead>
						<tr style="background: {whitelabel ? primarycolor : 'var(--primary)'}">
							{#each columns as column}
								<th on:click={() => {}}>
									<div>{column.column_name}</div>
								</th>
							{/each}
						</tr>
					</thead>
					<tbody>
						{#each data as dr}
							<tr
								style="cursor: {cursor}; border-color: {whitelabel
									? primarycolor
									: 'var(--primary)'}; border: none;"
								on:click={() => {
									rowClick(dr);
								}}
							>
								{#each columns as column}
									<td data-label={column.column_name} style="cursor: {cursor};">
										<div style="cursor: {cursor};">
											{#if 'pretexticon' in column}
												{column.pretexticon}
											{/if}
											{dr[column.column]}
										</div>
									</td>
								{/each}
							</tr>
						{/each}
					</tbody>
				{:else}
					<tbody>
						{#each groups as group}
							<tr
								style="cursor: {cursor}; border-color: {whitelabel
									? primarycolor
									: 'var(--primary)'}"
								on:click={() => {
									rowClick(group);
								}}
							>
								<td style="cursor: {cursor}; padding: 20px 20px">
									<div
										style="cursor: {cursor}; display: flex; gap: 20px; align-items: center; font-size: 16px;"
									>
										<Icon icon="fa-folder" />{group.name} ({group.count})
									</div>
								</td>
							</tr>
						{/each}
					</tbody>
				{/if}
			</table>
		{:else if imageTileView}
			<Row padding="15px" rowgap="25px" gap="25px" wrap="wrap">
				{#each data as dr}
					<!-- svelte-ignore a11y-click-events-have-key-events -->
					<!-- svelte-ignore a11y-no-static-element-interactions -->
					<div
						style="position: relative; border-radius: 5px; overflow: hidden; border: solid 1px {whitelabel
							? primarycolor
							: 'var(--primary)'}; height: 200px; width: 200px; min-height: 200px; min-width: 200px; max-height: 200px; max-width: 200px; display: flex; align-items: center; justify-content: center; object-fit: cover;"
						on:click={() => {
							rowClick(dr);
						}}
					>
						<img
							src={imageBase + '/' + dr[imageColumn]}
							alt=""
							style="height: 100%; width: 100%; object-fit: cover;"
						/>
						<div
							style="padding: 10px; color: {dark
								? 'var(--darktext)'
								: whitelabel
								? primarycolor
								: 'var(--primary)'}; position: absolute; bottom: 10px; left: 10px; z-index: 3; border-radius: 5px; background: {dark
								? 'rgb(40, 40, 40)'
								: 'white'}"
						>
							{dr[altColumn]}
						</div>
					</div>
				{/each}
			</Row>
		{:else if leadsView}
			<Row padding="15px" rowgap="25px" gap="25px" wrap="wrap">
				{#each data as dr}
					<!-- svelte-ignore a11y-click-events-have-key-events -->
					<!-- svelte-ignore a11y-no-static-element-interactions -->
					<div
						style="position: relative; border-radius: 5px; border: solid 1px {whitelabel
							? primarycolor
							: 'var(--primary)'}; height: fit-content; width: 300px; height: fit-content; padding: 15px; display: flex; flex-direction: column; gap: 10px;"
						on:click={() => {
							rowClick(dr);
						}}
					>
						<div
							style="height: 25px; display: flex; gap: 15px; align-items: center; color: {dark
								? 'var(--darktext)'
								: 'initial'}"
						>
							<Icon icon="fa-clipboard" />
							<span style="font-weight: 500;">{dr['name']}</span>
						</div>
						<div
							style="display: flex; gap: 15px; align-items: center; color: {dark
								? 'var(--darktext)'
								: 'initial'}"
						>
							<Icon icon="fa-envelope" />

							<a href="mailto:{dr['email']}" style="color: {dark ? 'var(--darktext)' : 'initial'}"
								>{dr['email']}</a
							>
						</div>
						<div
							style="display: flex; gap: 15px; align-items: center; color: {dark
								? 'var(--darktext)'
								: 'initial'}"
						>
							<Icon icon="fa-phone" />
							<a href="tel:{dr['phone']}" style="color: {dark ? 'var(--darktext)' : 'initial'}"
								>{dr['phone']}</a
							>
						</div>

						<div
							style="display: flex; gap: 15px; margin-top: 25px; margin-left: 15px; color: {dark
								? 'var(--darktext)'
								: 'initial'}"
						>
							<Icon icon="fa-message" />
							{dr['message']}
						</div>

						<div
							style="display: flex; margin-top: auto; padding-top: 25px; color: {dark
								? 'var(--darktext)'
								: 'initial'}"
						>
							{dr['date']}
							<Row marginleft="auto">
								{#if dr == data[0]}
									<span style="font-weight: 500;">newest</span>
								{/if}
							</Row>
						</div>
					</div>
				{/each}
			</Row>
		{:else if rocketsView}
			{#each data as dr}
				<Column
					borderradius="5px"
					border="solid 1px {whitelabel ? primarycolor : 'var(--primary)'}"
					padding="20px"
					gap="20px"
				>
					<Row align="center" gap="20px" cursor="pointer" on:click={() => { selectedRocket = dr; rocketNameDialog.openDialog() }}>
						<Icon color={dark ? 'var(--darktext)' : 'black'} icon="fa-rocket" size="fa-2xl" />
						<div style="font-size: 24px; color: {dark ? 'var(--darktext)' : 'black'}">
							{dr.rocketname}
						</div>
					</Row>

					<Row
						border="solid 1px rgb(240,240,240)"
						width="calc(100% - 20px)"
						padding="10px"
						borderradius="5px"
						cursor="pointer"
						on:click={() => { selectedRocket = dr; rocketDescriptionDialog.openDialog() }}
					>
						{#if dr.rocketdescription.trim() == ''}
							<div style="color: rgb(150,150,150)">Add description</div>
						{:else}
							<div style="color: {dark ? 'var(--darktext)' : 'black'};">
								{dr.rocketdescription}
							</div>
						{/if}
					</Row>

					<Row width="100%" margintop="20px" gap="25px">
						<!-- svelte-ignore a11y-click-events-have-key-events -->
						<!-- svelte-ignore a11y-no-static-element-interactions -->
						<div style="flex-grow: 1; font-size: 14px; cursor: pointer; color: {dark ? 'var(--darktext)' : 'black'}" on:click={() => { selectedRocket = dr; rocketChatDialog.openDialog(); document.getElementById('rocketchatinput')?.focus();  }}>Rocket Chat</div>

						<div style="flex-grow: 1; font-size: 14px; color: {dark ? 'var(--darktext)' : 'black'}">Pin to Quick Launch</div>

						<div style="font-size: 14px; color: {dark ? 'var(--darktext)' : 'black'}">
							{dr.rocketstatus}
						</div>
					</Row>
				</Column>
			{/each}
		{/if}
	</div>
</div>

<style type="text/css">
	@media screen and (max-width: 1000px) {
		table thead {
			display: none;
		}
		table td {
			display: flex;
		}

		table tbody {
			display: flex;
			flex-direction: column;
			gap: 2px;
		}

		table td::before {
			content: attr(data-label);
			font-weight: bold;
			width: 120px;
			min-width: 120px;
		}

		.ktomek-table tbody tr:hover > td::before {
			color: white;
		}

		.ktomek-table tbody tr:first-child {
			border-top: 2px solid;
		}
	}

	.ktomek-table tbody tr:hover > td {
		background: rgb(225, 225, 225);
	}

	.ktomek-dark-table-wrapper::-webkit-scrollbar {
		width: 16px;
	}

	.ktomek-dark-table-wrapper::-webkit-scrollbar-track {
		background-color: transparent;
		border: 0 solid transparent;
	}

	.ktomek-dark-table-wrapper::-webkit-scrollbar-thumb {
		border-radius: 8px;
		border: 3px solid transparent;
		background-clip: content-box;
		background-color: var(--darktext) !important;
	}

	.ktomek-table-wrapper::-webkit-scrollbar {
		width: 16px;
	}

	.ktomek-table-wrapper::-webkit-scrollbar-track {
		background-color: transparent;
		border: 0 solid transparent;
	}

	.ktomek-table-wrapper::-webkit-scrollbar-thumb {
		border-radius: 8px;
		border: 3px solid transparent;
		background-clip: content-box;
		background-color: var(--primary);
	}

	.ktomek-table {
		border-collapse: collapse;
		margin: 20px 10px;
		font-size: 0.9em;
		font-family: sans-serif;
		min-width: 300px;
		box-shadow: 0 0 20px rgba(0, 0, 0, 0.15);
		flex-grow: 1;
		border-radius: 5px;
		overflow: hidden;
		overflow-x: hidden;

		max-height: 100%;
	}

	.ktomek-table thead tr {
		color: #ffffff;
		text-align: left;
	}

	.ktomek-table th,
	.ktomek-table td {
		padding: 12px 15px;
		transition: all 150ms;
	}

	.ktomek-dark-table th,
	.ktomek-dark-table td {
		padding: 12px 15px;
		color: var(--darktext);
		transition: all 150ms;
	}

	.ktomek-table tbody tr {
		border-bottom: 1px solid #dddddd;
	}

	.ktomek-table tbody tr {
		border-top: 1px solid #dddddd;
	}

	.ktomek-table tbody tr:nth-of-type(even) {
		background-color: #f3f3f3;
	}

	.ktomek-table tbody tr:nth-of-type(odd) {
		background-color: white;
	}

	.ktomek-dark-table tbody tr:nth-of-type(even) {
		background-color: rgb(100, 100, 100);
	}

	.ktomek-dark-table tbody tr:nth-of-type(odd) {
		background-color: rgb(60, 60, 60);
	}

	.ktomek-table tbody tr:last-of-type {
		border-bottom: 2px solid;
	}

	.ktomek-table tbody tr.active-row {
		font-weight: bold;
		color: #009879;
	}
</style>
