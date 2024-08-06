<script>
	// @ts-nocheck

	export let name = '';
	export let width = '1rem';
	export let height = '1rem';
	export let cssclass = '';
	let icons = [
		{
			box: 24,
			name: 'vault',
			svg: `<g style="transform: scale(0.25)">
        <circle width="100" height="100" fill="white" />
        <circle cx="50" cy="50" r="44.3" fill="#464646" />
        <circle cx="50" cy="50" r="39.1" fill="#683F3F" />
        <circle cx="21.45" cy="19.65" r="1.75" fill="#212121" />
        <circle cx="49.95" cy="8.45" r="1.75" fill="#212121" />
        <circle cx="49.95" cy="91.55" r="1.75" fill="#212121" />
        <circle cx="91.75" cy="49.95" r="1.75" fill="#212121" />
        <circle cx="8.25" cy="49.95" r="1.75" fill="#212121" />
        <circle cx="78.35" cy="19.65" r="1.75" fill="#212121" />
        <circle cx="78.35" cy="80.55" r="1.75" fill="#212121" />
        <circle cx="21.45" cy="80.55" r="1.75" fill="#212121" />
    </g>

    <g style="transform: scale(0.25)">
        <circle cx="49.9" cy="50.3" r="19.1" fill="#D9D9D9" />
        <circle cx="49.9" cy="50.3" r="2.9" fill="#030303" />
        <rect x="48.5" y="19.4" width="2.7" height="22.2" rx="1.35" fill="#D9D9D9" />
        <rect y="48.5" x="19.4" height="2.7" width="22.2" rx="1.35" fill="#D9D9D9" />
        <rect y="0" x="45" height="2.7" width="22.2" style="transform: rotate(45deg);"
            fill="#D9D9D9" />
        <rect y="0" x="75" height="2.7" width="22.2" style="transform: rotate(45deg);"
            fill="#D9D9D9" />
        <rect y="5" x="70" height="22.2" width="2.7" style="transform: rotate(45deg);"
            fill="#D9D9D9" />
        <rect y="70" x="5" height="2.7" width="22.2" style="transform: rotate(-45deg);"
            fill="#D9D9D9" />
        <rect y="48.5" x="59.0" height="2.7" width="22.2" rx="1.35" fill="#D9D9D9" />
        <rect x="48.5" y="59.0" width="2.7" height="22.2" rx="1.35" fill="#D9D9D9" />
    </g>`
		}
	];
	let displayIcon = icons.find((e) => e.name === name);
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div on:click>
    <svg style="cursor: pointer;" class={cssclass} {width} {height} viewBox="0 0 {displayIcon.box} {displayIcon.box}"
	>{@html displayIcon.svg}</svg>
</div>

