<script lang="ts">
	export let id = "";
    export let name = "";
    export let required = false;
    export let placeholder = " ";
	export let value = "";
	export let disabled = false;

    export let background = "white";
</script>

<div class="textbox">
	<input style="background: {background};" type="date" id="{id}" name="{name}" placeholder="{placeholder}" disabled={disabled} required={required} bind:value={value} on:change on:keyup on:focus/>
	<label style="background: {background};" for="{id}"><slot /></label>
</div>

<style type="text/css">
	.textbox {
		display: flex;
		position: relative;
		padding: 0px 20px;
		-webkit-transition: all 150ms;
		-o-transition: all 150ms;
		transition: all 150ms;
        flex-grow: 1;
	}

	.textbox label {
		position: absolute;
		top: 50%;
		-webkit-transform: translateY(-50%);
		-ms-transform: translateY(-50%);
		transform: translateY(-50%);
		left: 30px;
		color: var(--light-text);
		-webkit-transition: all 150ms;
		-o-transition: all 150ms;
		transition: all 150ms;
		padding: 10px 15px;
		font-size: 16px;
		cursor: text;
		border-radius: 5px;
	}

	.textbox input {
		border: solid 1px var(--light-text);
		outline: 0;
		border-radius: 5px;
		height: 45px;
		-webkit-box-flex: 1;
		-ms-flex-positive: 1;
		flex-grow: 1;
		padding: 0px 10px;
		padding-top: 5px;
		font-size: 14px;
		transition: all 150ms;
		padding-top: 10px;
	}

	.textbox input::-webkit-input-placeholder {
		opacity: 0;
	}

	.textbox input::-moz-placeholder {
		opacity: 0;
	}

	.textbox input:-ms-input-placeholder {
		opacity: 0;
	}

	.textbox input::-ms-input-placeholder {
		opacity: 0;
	}

	.textbox input::placeholder {
		opacity: 0;
	}

	.textbox input + label {
		top: 0;
	}

	.textbox input:not(:-moz-placeholder-shown):not(:focus) + label {
		opacity: 1;
	}

	.textbox input:not(:-ms-input-placeholder):not(:focus) + label {
		opacity: 1;
	}

	.textbox input:not(:placeholder-shown):not(:focus) + label {
		opacity: 1;
	}

	.textbox input:is(:placeholder-shown):is(:focus)::-webkit-input-placeholder {
		opacity: 1;
	}

	.textbox input:is(:placeholder-shown):is(:focus)::-moz-placeholder {
		opacity: 1;
	}

	.textbox input:is(:placeholder-shown):is(:focus):-ms-input-placeholder {
		opacity: 1;
	}

	.textbox input:is(:placeholder-shown):is(:focus)::-ms-input-placeholder {
		opacity: 1;
	}

	.textbox input:is(:-moz-placeholder-shown):is(:focus)::placeholder {
		opacity: 1;
	}

	.textbox input:is(:-ms-input-placeholder):is(:focus)::placeholder {
		opacity: 1;
	}

	.textbox input:is(:placeholder-shown):is(:focus)::placeholder {
		opacity: 1;
	}
</style>
