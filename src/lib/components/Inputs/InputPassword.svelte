<script>
	import InputWrapper from './InputWrapper.svelte';
	//Exports
	export let id;
	export let value = '';
	export let placeholder = '';
	export let required = true;
	export let validation = {
		valid: true,
		message: ''
	};

	let passwordField;
	let showPassword = false;
	const toggleShowPassword = () => {
		const { type } = passwordField;
		if (type === 'password') {
			showPassword = true;
			passwordField.type = 'text';
		} else {
			showPassword = false;
			passwordField.type = 'password';
		}
	};
</script>

<InputWrapper {id} bind:validation>
	<input
		{id}
		type="password"
		bind:value
		on:input
		{placeholder}
		{required}
		class="peer w-full py-0 px-[5px] h-10 border-none bg-none outline-none"
		bind:this={passwordField}
	/>
	<button
		tabindex="-1"
		type="button"
		on:click={toggleShowPassword}
		class="absolute top-1/2 right-[5px] -translate-y-1/2 h-8 w-8 border-none"
	>
		<img src={showPassword ? '/hide.ico' : '/show.ico'} alt={id} />
	</button>

	<svelte:fragment slot="label-text">
		<slot />
	</svelte:fragment>
</InputWrapper>

<style>
	input[type='password']::-ms-reveal {
		display: none;
	}
</style>
