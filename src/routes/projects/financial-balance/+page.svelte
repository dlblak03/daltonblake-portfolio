<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import Row from '$lib/Containers/Row.svelte';
	import Icon from '$lib/Graphics/Icon.svelte';
	import { dark } from '../../ui_store';

	let selectedMenuItem = 'Budget';

	let activeINLevel = 1;
	let activeOUTLevel = 1;

	const incomeObject = {
		name: 'Income',
		type: 'folder',
		budget: 2500,
		icon: 'money-bill-wave',
		showTransactions: false,
		children: [
			{
				name: 'Monthly Salary',
				type: 'transaction',
				amount: 2500,
				date: '01.12.2024'
			}
		]
	};

	const expenseObject = {
		name: 'Budget',
		type: 'folder',
		budget: 2500,
		icon: 'table',
		children: [
			{
				name: 'Food',
				type: 'folder',
				budget: 300,
				icon: 'pot-food',
				showTransactions: false,
				children: [
					{
						name: 'Week 1 Groceries',
						type: 'transaction',
						amount: 75,
						date: '01.12.2024'
					},
					{
						name: 'Week 2 Groceries',
						type: 'transaction',
						amount: 75,
						date: '08.12.2024'
					},
					{
						name: 'Week 3 Groceries',
						type: 'transaction',
						amount: 75,
						date: '16.12.2024'
					},
					{
						name: 'Week 4 Groceries',
						type: 'transaction',
						amount: 75,
						date: '24.12.2024'
					}
				]
			},
			{
				name: 'Housing',
				type: 'folder',
				budget: 880,
				icon: 'house',
				showTransactions: false,
				children: [
					{
						name: 'Rent',
						type: 'transaction',
						amount: 750,
						date: '01.12.2024'
					},
					{
						name: 'Renter Insurance',
						type: 'transaction',
						amount: 5,
						date: '01.12.2024'
					},
					{
						name: 'Electrics',
						type: 'transaction',
						amount: 65,
						date: '01.12.2024'
					},
					{
						name: 'Radio & TV',
						type: 'transaction',
						amount: 20,
						date: '01.12.2024'
					},
					{
						name: 'Internet',
						type: 'transaction',
						amount: 40,
						date: '01.12.2024'
					}
				]
			},
			{
				name: 'Medical',
				type: 'folder',
				budget: 20,
				icon: 'notes-medical',
				showTransactions: false,
				children: [
					{
						name: 'Medication',
						type: 'transaction',
						amount: 20,
						date: '01.12.2024'
					}
				]
			},
			{
				name: 'Personal',
				type: 'folder',
				budget: 100,
				icon: 'user',
				showTransactions: false,
				children: [
					{
						name: 'Hobbies',
						type: 'transaction',
						amount: 50,
						date: '01.12.2024'
					},
					{
						name: 'Shopping',
						type: 'transaction',
						amount: 50,
						date: '01.12.2024'
					}
				]
			},
			{
				name: 'Pets',
				type: 'folder',
				budget: 150,
				icon: 'paw',
				showTransactions: false,
				children: [
					{
						name: 'Food & Treats',
						type: 'transaction',
						amount: 100,
						date: '01.12.2024'
					},
					{
						name: 'Supplies',
						type: 'transaction',
						amount: 50,
						date: '01.12.2024'
					}
				]
			},
			{
				name: 'Savings',
				type: 'folder',
				budget: 970,
				icon: 'piggy-bank',
				showTransactions: false,
				children: [
					{
						name: 'Savings Transfer',
						type: 'transaction',
						amount: 970,
						date: '01.12.2024'
					}
				]
			},
			{
				name: 'Services',
				type: 'folder',
				budget: 20,
				icon: 'wrench',
				showTransactions: false,
				children: [
					{
						name: 'Apple Subscription',
						type: 'transaction',
						amount: 20,
						date: '01.12.2024'
					}
				]
			},
			{
				name: 'Transportation',
				type: 'folder',
				budget: 60,
				icon: 'car',
				showTransactions: false,
				children: [
					{
						name: 'Train Card',
						type: 'transaction',
						amount: 60,
						date: '01.12.2024'
					}
				]
			}
		]
	};
</script>

<Column dark={$dark} gap="75px" minwidth="100%" maxwidth="100%" alignitems="center">
	<div class="financial-tracker-container">
		<div class="financial-items-column" id="lineItemsColumn">
			<Row
				grow="0"
				background="transparent"
				alignitems="center"
				justifycontent="center"
				wrap="flex-wrap"
				minwidth="100%"
				maxwidth="100%"
				margin="0 0 25px 0"
			>
				<header class="header">
					<h1 style="color: {$dark ? 'var(--darktext)' : 'var(--primary)'};" class="title">
						Financial Balance: Track, Manage, and Grow
					</h1>
					<p class="subtitle">
						Stay on top of your budget and income for a balanced financial life
					</p>
				</header>
			</Row>

			<Row
				grow="0"
				background="transparent"
				alignitems="center"
				justifycontent="center"
				wrap="flex-wrap"
				minwidth="100%"
				maxwidth="100%"
				margin="0 0 25px 0"
				border="solid 1px var(--primary)"
				borderradius="5px"
			>
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<!-- svelte-ignore a11y-no-static-element-interactions -->
				<div
					on:click={() => {
						selectedMenuItem = 'Budget';
					}}
					class="menu-item {$dark && selectedMenuItem != 'Budget'
						? 'dark-menu-item'
						: ''} {selectedMenuItem == 'Budget' ? 'selected-menu-item' : ''}"
				>
					Budget
				</div>

				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<!-- svelte-ignore a11y-no-static-element-interactions -->
				<div
					on:click={() => {
						selectedMenuItem = 'Actual';
					}}
					class="menu-item {$dark && selectedMenuItem != 'Actual'
						? 'dark-menu-item'
						: ''} {selectedMenuItem == 'Actual' ? 'selected-menu-item' : ''}"
				>
					Actual
				</div>
			</Row>

			{#if selectedMenuItem == 'Budget'}
				{#if activeINLevel == 1}
					<!-- svelte-ignore a11y-click-events-have-key-events -->
					<!-- svelte-ignore a11y-no-static-element-interactions -->
					<div
						on:click={() => {
							incomeObject.showTransactions = !incomeObject.showTransactions;
						}}
						class="financial-item-card {$dark ? 'dark-card' : ''}"
					>
						<div style="display: flex; align-items: center; width: 100%; gap: 15px;">
							<Icon
								color={$dark ? 'var(--darktext)' : 'var(--primary)'}
								icon="fa-{incomeObject.icon}"
								size="fa-xl"
							/>
							<h3>{incomeObject.name}</h3>
							<p>{incomeObject.budget}€</p>
						</div>

						<div
							style="display: flex; width: 100%; transform: scale({incomeObject.showTransactions
								? '1'
								: '0'}); max-height: {incomeObject.showTransactions
								? '10000'
								: '0'}px; transition: all 150ms;"
						>
							<table style="margin-top: 15px;" class="stats-table {$dark ? 'dark-table' : ''}">
								<thead>
									<tr>
										<th>Item</th>
										<th>Amount</th>
										<th>Date</th>
									</tr>
								</thead>
								<tbody>
									{#each incomeObject.children as child}
										<tr>
											<td style="width: 40%;">{child.name}</td>
											<td style="width: 30%;">{child.amount}€</td>
											<td style="width: 30%;">{child.date}</td>
										</tr>
									{/each}
									<tr>
										<td colspan="3"
											><Icon
												color={$dark ? 'var(--darktext)' : 'var(--primary)'}
												icon="fa-light fa-plus"
												size="fa-lg"
												margin="0 10px 0 0"
											></Icon>Add Item</td
										>
									</tr>
								</tbody>
							</table>
						</div>
					</div>
				{/if}

				<div class="income-expenses-divider">
					<hr />
				</div>

				{#if activeOUTLevel == 1}
					{#each expenseObject.children as child}
						<!-- svelte-ignore a11y-click-events-have-key-events -->
						<!-- svelte-ignore a11y-no-static-element-interactions -->
						<div
							on:click={() => {
								child.showTransactions = !child.showTransactions;
							}}
							class="financial-item-card {$dark ? 'dark-card' : ''}"
						>
							<div style="display: flex; align-items: center; width: 100%; gap: 15px;">
								<Icon
									color={$dark ? 'var(--darktext)' : 'var(--primary)'}
									icon="fa-{child.icon}"
									size="fa-xl"
								/>
								<h3>{child.name}</h3>
								<p>{child.budget}€</p>
							</div>

							<div
								style="display: flex; width: 100%; transform: scale({child.showTransactions
									? '1'
									: '0'}); max-height: {child.showTransactions
									? '10000'
									: '0'}px; transition: all 150ms;"
							>
								<table style="margin-top: 15px;" class="stats-table {$dark ? 'dark-table' : ''}">
									<thead>
										<tr>
											<th>Item</th>
											<th>Amount</th>
											<th>Date</th>
										</tr>
									</thead>
									<tbody>
										{#each child.children as childTwo}
											<tr>
												<td style="width: 40%;">{childTwo.name}</td>
												<td style="width: 30%;">{childTwo.amount}€</td>
												<td style="width: 30%;">{childTwo.date}</td>
											</tr>
										{/each}
										<tr>
											<td colspan="3"
												><Icon
													color={$dark ? 'var(--darktext)' : 'var(--primary)'}
													icon="fa-light fa-plus"
													size="fa-lg"
													margin="0 10px 0 0"
												></Icon>Add Item</td
											>
										</tr>
									</tbody>
								</table>
							</div>
						</div>
					{/each}
				{/if}

				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<!-- svelte-ignore a11y-no-static-element-interactions -->
				<div
					on:click={() => {}}
					style="margin-top: 25px; background: var(--primary);"
					class="financial-item-card {$dark ? 'dark-card' : ''}"
				>
					<div style="display: flex; align-items: center; width: 100%; gap: 15px;">
						<h3 style="color: var(--darktext)">Surplus/Deficit</h3>
						<p style="color: var(--darktext)">- €</p>
					</div>
				</div>
			{/if}
		</div>
	</div>
</Column>

<style>
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

	.menu-item {
		display: flex;
		align-items: center;
		justify-content: center;
		flex-grow: 1;
		height: 100%;
		padding: 15px 0;
		cursor: pointer;
		font-size: 1.2rem;
		font-weight: bold;
		color: var(--primary);
		transition: all 150ms;
	}

	.dark-menu-item {
		color: var(--darktext);
	}

	.menu-item:hover {
		background: var(--primary);
		color: var(--darktext);
	}

	.menu-item:first-child {
		border-right: solid 1px var(--primary);
	}

	.selected-menu-item {
		background: var(--primary);
		color: var(--darktext);
	}

	/* Financial Tracker Container */
	.financial-tracker-container {
		max-width: 1000px;
		margin: 0;
		width: 100%;
		margin-bottom: 25px;
	}

	/* Financial Items Column */
	.financial-items-column {
		display: flex;
		flex-direction: column;
		gap: 20px;
		margin-bottom: 25px;

		padding: 0 20px;

		width: calc(100% - 40px);
	}

	/* Financial Item Card Styles */
	.financial-item-card {
		background-color: #fff;
		padding: 10px 20px;
		border-radius: 10px;

		border: 2px solid #ddd;
		transition: all 150ms;

		width: calc(100% - 40px);

		display: flex;
		align-items: center;
		cursor: pointer;
		flex-direction: column;
	}

	.dark-card {
		background-color: #333;
		border: 2px solid #4c4c4c;
	}

	.financial-item-card:hover {
		border-color: var(--primary);
		transform: translateY(-5px);
	}

	.dark-card:hover {
		border-color: var(--darktext);
	}

	/* Financial Item Title */
	.financial-item-card h3 {
		font-size: 1.3rem;
		color: var(--primary);
		margin-bottom: 10px;
		margin-top: 10px;
		transition: all 150ms;
	}

	.dark-card h3 {
		color: var(--darktext);
	}

	/* Financial Item Description */
	.financial-item-card p {
		font-size: 1.1rem;
		color: #666;
		transition: all 150ms;
		margin-left: auto;
	}

	.dark-card p {
		color: #bababa;
	}

	/* Tags */
	.financial-item-card .tags {
		margin-bottom: 25px;
		margin-top: 25px;
		margin-left: -5px;
		white-space: pre-wrap;
		display: flex;
		flex-wrap: wrap;
		transition: all 150ms;
	}

	.financial-item-card .tags span {
		background-color: #ddd;
		padding: 5px 10px;
		border-radius: 5px;
		font-size: 0.9rem;
		margin: 5px;
		transition: all 150ms;
	}

	/* Link */
	.financial-item-card a {
		font-size: 1.1rem;
		color: var(--primary);
		text-decoration: none;
		font-weight: bold;
		transition: all 150ms;
	}

	.dark-card a {
		color: var(--darktext);
	}

	.financial-item-card a:hover {
		text-decoration: underline;
		transition: all 150ms;
	}

	@media (max-width: 768px) {
		.financial-item-card h3 {
			font-size: 1.2rem;
		}

		.financial-item-card p {
			font-size: 0.85rem;
		}

		.financial-item-card .tags span {
			font-size: 0.7rem;
		}

		.financial-item-card a {
			font-size: 0.9rem;
		}
	}

	@media (max-width: 480px) {
		h1 {
			font-size: 1.3rem;
		}

		.financial-item-card h3 {
			font-size: 1.2rem;
		}

		.financial-item-card p {
			font-size: 0.8rem;
		}

		.financial-item-card .tags span {
			font-size: 0.7rem;
		}

		.financial-item-card a {
			font-size: 0.8rem;
		}
	}

	hr {
		border: 0;
		border-top: 2px solid #ddd;
		width: 100%;
		margin: 10px auto;
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
		width: fit-content;
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

	.toggle-links {
		margin-bottom: 20px;
	}

	.view-link {
		font-size: 18px;
		margin: 0 15px;
		cursor: pointer;
		padding: 10px;
		color: #4caf50;
		font-weight: bold;
	}

	.view-link:hover {
		background-color: #e1e1e1;
		border-radius: 5px;
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
