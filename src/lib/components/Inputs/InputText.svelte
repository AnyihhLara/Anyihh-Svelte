<script>
	import InputWrapper from './InputWrapper.svelte';
	//Exports
	export let id;
	export let value = '';
	export let placeholder = '';
	export let required = false;
	export let validation = {
		valid: true,
		message: ''
	};
</script>

<InputWrapper {id} bind:validation>
	<input
		{id}
		type="text"
		bind:value
		on:input
		{placeholder}
		{required}
		class="peer w-full py-0 px-[5px] h-10 border-none bg-none outline-none"
	/>
	<svelte:fragment slot="label-text">
		<slot />
	</svelte:fragment>
</InputWrapper>
