<script>
// @ts-nocheck

	export let buttonType = 'primary';
	export let color = 'default';
	export let width = 'fit-content';

	export let disabled = false;
	export let inverse = false;
	export let active = false;
</script>

<button style="color: {color}; width: {width}" class={buttonType + ' ' + (active ? 'active': '')} class:disabled={disabled} class:inverse={inverse} on:click>
	<slot />
</button>

<style>
	button {
		text-transform: uppercase;
		height: 50px;
		outline: none;
		background: none;
		letter-spacing: 0.2rem;
		font-weight: 500;
		cursor: pointer;
		font-size: 16px;
		transition: all 300ms;
		border-radius: 5px;
		border: solid 2px transparent;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 20px
	}

	.primary {
		color: var(--primary);
	}

    .primary:hover {
		color: var(--primary);
        border-color: var(--primary);
        padding: 0 20px;
	}

	.active {
		color: var(--primary);
        border-color: var(--primary);
        padding: 0 20px;
	}

	.primary.disabled {
		pointer-events: none;
		background-color: whitesmoke;
		color: lightgrey;
	}

	.primary.inverse {
		color: white;
	}

	.primary.inverse:hover {
		color: white;
        border-color: white;
        padding: 0 20px;
	}

	.success {
		color: white;
		border-color: transparent;
	}

    .success:hover {
		color: white !important;
        border-color: white;
        padding: 0 20px;
		background: var(--success)
	}

	.success.disabled {
		pointer-events: none;
		background-color: whitesmoke;
		color: lightgrey;
	}

	.success.inverse {
		color: white;
	}

	.success.inverse:hover {
		color: white;
        border-color: white;
        padding: 0 20px;
	}

	.warn {
		color: white;
	}

    .warn:hover {
		color: white !important;
        border-color: white;
        padding: 0 20px;
		background: var(--warn)
	}

	.warn.disabled {
		pointer-events: none;
		background-color: whitesmoke;
		color: lightgrey;
	}

	.warn.inverse {
		color: white;
	}

	.warn.inverse:hover {
		color: white;
        border-color: white;
        padding: 0 20px;
	}

    .link {
        font-size: 12px;
        color: inherit;
        text-decoration: none;
    }

    .link:hover {
		color: var(--primary);
        text-decoration: underline;
	}
</style>
