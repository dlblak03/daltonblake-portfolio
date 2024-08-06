<script lang="ts">
    export let type = 'text';
	export let id = '';
    export let name = '';
    export let required = false;
    export let placeholder = " ";
	export let value = "";
	export let pattern = '.{0,}';
	export let dark = false;
	export let disabled = false;
	export let whitelabel = false;
	export let primarycolor = '#540000'
	export let rows = 4
	export let transition = 'all 150ms'
	export let hideLabel = false;
</script>

<div class="textbox">
	<textarea rows="{rows}" disabled={disabled} on:focus style="transition: {transition}; background: {dark ? 'rgb(60,60,60)' : 'white'}; min-height: 40px; max-height: 500px; overflow: hidden; resize: none; border-color: {whitelabel ? primarycolor : 'var(--primary)'}; color: {dark ? 'var(--darktext)' : 'initial'};" id="{id}" name="{name}" placeholder="{placeholder}" required={required} bind:value={value} on:change on:keyup/>
	<label style="display: {hideLabel ? 'none' : 'flex'}; background: {dark ? 'rgb(60,60,60)' : 'white'}; border-color: {dark ? whitelabel ? primarycolor : 'var(--primary)' : 'white'}; color: {dark ? 'var(--darktext)' : 'initial'};" for="{id}"><slot /></label>
</div>

<style type="text/css">
	.textbox {
		display: -webkit-box;
		display: -ms-flexbox;
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
		-webkit-transition: all 150ms;
		-o-transition: all 150ms;
		transition: all 150ms;
		padding: 10px 15px;
		font-size: 16px;
		cursor: text;
		border-radius: 5px;
	}

	.textbox textarea {
		border: solid 1px;
		outline: 0;
		border-radius: 5px;
		-webkit-box-flex: 1;
		-ms-flex-positive: 1;
		flex-grow: 1;
		padding: 0px 10px;
		padding-top: 5px;
		font-size: 14px;
		transition: all 150ms;
		padding-top: 25px;
		resize: vertical
	}

	.textbox textarea::-webkit-input-placeholder {
		opacity: 0;
	}

	.textbox textarea::-moz-placeholder {
		opacity: 0;
	}

	.textbox textarea:-ms-input-placeholder {
		opacity: 0;
	}

	.textbox textarea::-ms-input-placeholder {
		opacity: 0;
	}

	.textbox textarea::placeholder {
		opacity: 0;
	}

	.textbox textarea + label {
		top: 0;
	}

	.textbox textarea:not(:-moz-placeholder-shown):not(:focus) + label {
		opacity: 1;
	}

	.textbox textarea:not(:-ms-input-placeholder):not(:focus) + label {
		opacity: 1;
	}

	.textbox textarea:not(:placeholder-shown):not(:focus) + label {
		opacity: 1;
	}

	.textbox textarea:is(:placeholder-shown):is(:focus)::-webkit-input-placeholder {
		opacity: 1;
	}

	.textbox textarea:is(:placeholder-shown):is(:focus)::-moz-placeholder {
		opacity: 1;
	}

	.textbox textarea:is(:placeholder-shown):is(:focus):-ms-input-placeholder {
		opacity: 1;
	}

	.textbox textarea:is(:placeholder-shown):is(:focus)::-ms-input-placeholder {
		opacity: 1;
	}

	.textbox textarea:is(:-moz-placeholder-shown):is(:focus)::placeholder {
		opacity: 1;
	}

	.textbox textarea:is(:-ms-input-placeholder):is(:focus)::placeholder {
		opacity: 1;
	}

	.textbox textarea:is(:placeholder-shown):is(:focus)::placeholder {
		opacity: 1;
	}
</style>
