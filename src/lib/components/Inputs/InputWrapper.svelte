<script>
	import InputError from './InputError.svelte';
	import InputLabel from './InputLabel.svelte';
	export let id;
	export let validation = {
		valid: true,
		message: ''
	};
	$: console.log(id, validation);
</script>

<div class="relative border-solid border-b border-b-neutral-400 mx-0 mt-[30px] mb-[15px]">
	<slot />
	<InputLabel forID={id}>
		<slot name="label-text" />
	</InputLabel>
</div>

{#if !validation.valid}
	<InputError>{validation.message}</InputError>
{/if}
