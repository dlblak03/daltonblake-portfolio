<script>
	// @ts-nocheck

	export let name = '';
	export let width = '1rem';
	export let height = '1rem';
	export let cssclass = '';
	export let background = '#002d59';
	export let cursor = 'pointer';
	export let border = 'none';
	let icons = [
		{
			box: 24,
			name: 'vault',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_banking_icon.png`
		},
		{
			box: 24,
			name: 'health',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_health_icon.png`
		},
		{
			box: 24,
			name: 'housing',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_housing_icon.png`
		},
		{
			box: 24,
			name: 'pets',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_pets_icon.png`
		},
		{
			box: 24,
			name: 'transportation',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_transportation_icon.png`
		},
		{
			box: 24,
			name: 'journal',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_journal_icon.png`
		},
		{
			box: 24,
			name: 'achievements',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_achievements_icon.png`
		},
		{
			box: 24,
			name: 'cat',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_cat_icon.png`
		},
		{
			box: 24,
			name: 'breakfast',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_breakfast_icon.png`
		},
		{
			box: 24,
			name: 'dinner',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_dinner_icon.png`
		},
		{
			box: 24,
			name: 'fish',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_fish_icon.png`
		},
		{
			box: 24,
			name: 'mammal',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_mammal_icon.png`
		},
		{
			box: 24,
			name: 'bird',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_bird_icon.png`
		},
		{
			box: 24,
			name: 'reptile',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_reptile_icon.png`
		},
		{
			box: 24,
			name: 'organizations',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_organization_icon.png`
		},
		{
			box: 24,
			name: 'users',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_users_icon.png`
		},
		{
			box: 24,
			name: 'role',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_role_icon.png`
		},
		{
			box: 24,
			name: 'applications',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_applications_icon.png`
		},
		{
			box: 24,
			name: 'lead',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_lead_icon.png`
		},
		{
			box: 24,
			name: 'timesheet',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_timesheet_icon.png`
		},
		{
			box: 24,
			name: 'socialmedia',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_social_media_icon.png`
		},
		{
			box: 24,
			name: 'mspsilver',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_msp_silver_icon.png`
		},
		{
			box: 24,
			name: 'mspgold',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_msp_gold_icon.png`
		},
		{
			box: 24,
			name: 'mspdiamond',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_msp_diamond_icon.png`
		},
		{
			box: 24,
			name: 'appdev',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_app_dev_icon.png`
		},
		{
			box: 24,
			name: 'seo',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_seo_icon.png`
		},
		{
			box: 24,
			name: 'mspbasic',
			url: `https://ik.imagekit.io/ktomek/images/ktomek_msp_basic_icon.png`
		},
		{
			box: 24,
			name: 'mspassets',
			url: 'https://ik.imagekit.io/ktomek/images/ktomek_assets_icon.png'
		},
		{
			box: 24,
			name: 'sapphire',
			url: 'https://ik.imagekit.io/ktomek/images/ktomek_sapphire_icon.png'
		},
		{
			box: 24,
			name: 'service_configuration',
			url: 'https://ik.imagekit.io/ktomek/images/ktomek_service_configuration_icon.png'
		},
		{
			box: 24,
			name: 'mspwebpages',
			url: 'https://ik.imagekit.io/ktomek/images/ktomek_webpages_icon.png'
		},
		{
			box: 24,
			name: 'rockets_building',
			url: 'https://ik.imagekit.io/ktomek/images/ktomek_building_icon.png'
		},
		{
			box: 24,
			name: 'rockets_launched',
			url: 'https://ik.imagekit.io/ktomek/images/ktomek_launched_icon.png'
		}
	];
	let displayIcon = icons.find((e) => e.name === name);
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div
	on:click
	style="height: {height}; width: {width}; border-radius: 100%; background: {background}; display: flex; align-items: center; justify-content: center; padding: 5px; border: {border}"
>
	{#if displayIcon.name == 'mspassets' || displayIcon.name == 'service_configuration' || displayIcon.name == 'mspwebpages'}
		<div style="border-radius: 5px; overflow: hidden; display: flex; align-items: center; justify-content: center; height: 22px; width: 22px;">
			<img
				style="height: 100%; cursor: {cursor}; object-fit: cover;"
				src={displayIcon.url}
				class={cssclass}
				viewBox="0 0 {displayIcon.box} {displayIcon.box}"
			/>
		</div>
		{:else if displayIcon.name == 'rockets_building' || displayIcon.name == 'rockets_launched'}
		<div style="border-radius: 5px; overflow: hidden; display: flex; align-items: center; justify-content: center; height: 27px; width: 27px;">
			<img
				style="height: 100%; cursor: {cursor}; object-fit: cover;"
				src={displayIcon.url}
				class={cssclass}
				viewBox="0 0 {displayIcon.box} {displayIcon.box}"
			/>
		</div>
	{:else}
		<img
			style="cursor: {cursor};"
			src={displayIcon.url}
			class={cssclass}
			{width}
			{height}
			viewBox="0 0 {displayIcon.box} {displayIcon.box}"
		/>
	{/if}
</div>
