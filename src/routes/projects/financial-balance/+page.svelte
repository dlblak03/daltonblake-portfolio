<script lang="ts">
	import Column from '$lib/Containers/Column.svelte';
	import Row from '$lib/Containers/Row.svelte';
	import Icon from '$lib/Graphics/Icon.svelte';
	import { dark } from '../../ui_store';

	let activeINLevel = 1;
	let activeOUTLevel = 1;

	const incomeObject = {
		name: 'Income',
		type: 'folder',
		budget: 2500,
		icon: 'money-bill-wave',
		children: []
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
				children: []
			},
			{
				name: 'Housing',
				type: 'folder',
				budget: 905,
				icon: 'house',
				children: []
			},
			{
				name: 'Medical',
				type: 'folder',
				budget: 20,
				icon: 'notes-medical',
				children: []
			},
			{
				name: 'Personal',
				type: 'folder',
				budget: 100,
				icon: 'user',
				children: []
			},
			{
				name: 'Pets',
				type: 'folder',
				budget: 150,
				icon: 'paw',
				children: []
			},
			{
				name: 'Savings',
				type: 'folder',
				budget: 945,
				icon: 'piggy-bank',
				children: []
			},
			{
				name: 'Services',
				type: 'folder',
				budget: 20,
				icon: 'wrench',
				children: []
			},
			{
				name: 'Transportation',
				type: 'folder',
				budget: 60,
				icon: 'car',
				children: []
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

			{#if activeINLevel == 1}
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<!-- svelte-ignore a11y-no-static-element-interactions -->
				<div on:click={() => {}} class="financial-item-card {$dark ? 'dark-card' : ''}">
					<Icon
						color={$dark ? 'var(--darktext)' : 'var(--primary)'}
						icon="fa-{incomeObject.icon}"
						size="fa-xl"
					/>
					<h3>{incomeObject.name}</h3>
					<p>{incomeObject.budget}€</p>
				</div>
			{/if}

			<div class="income-expenses-divider">
				<hr />
			</div>

			{#if activeOUTLevel == 1}
				{#each expenseObject.children as child}
					<!-- svelte-ignore a11y-click-events-have-key-events -->
					<!-- svelte-ignore a11y-no-static-element-interactions -->
					<div on:click={() => {}} class="financial-item-card {$dark ? 'dark-card' : ''}">
						<Icon
							color={$dark ? 'var(--darktext)' : 'var(--primary)'}
							icon="fa-{child.icon}"
							size="fa-xl"
						/>
						<h3>{child.name}</h3>
						<p>{child.budget}€</p>
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
				<h3 style="color: var(--darktext)">Surplus/Deficit</h3>
				<p style="color: var(--darktext)">- €</p>
			</div>
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
		gap: 15px;
		cursor: pointer;
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
</style>
