<script lang="ts">
	import { onMount } from "svelte";

	export let id: string;
	export let value: string | number = "";
	export let label = "Textbox";
	export let type: "text" | "email" | "password" | "number" = "text";
	export let required = true;
	export let disabled = false;
	export let error = false;
	export let grow = false;
	export let placeholder = label;

	let input: HTMLInputElement;

	onMount(() => {
		input.type = type;
	});
</script>

<div>
	<input
		{id}
		{disabled}
		{required}
		{placeholder}
		class:grow
		class:error
		bind:value
		bind:this={input}
	/>

	<label class:disabled for={id}>{label}</label>
</div>

<style lang="scss">
	@use "./textbox" as *;

	div {
		input {
			@include textbox-input;

			&.grow {
				width: 100%;
			}
		}

		label {
			@include textbox-label;
		}

		@include textbox-wrapper;
	}
</style>
