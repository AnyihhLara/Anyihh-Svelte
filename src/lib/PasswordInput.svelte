<script>
	//Exports
	export let hidePassError;
	export let identifier;
	export let label;
	export let showPassword;
	export let toggleShowPassword;
	export let value;

	//Variables
	let style = 'peer w-full py-0 px-[5px] h-10 border-none bg-none outline-none';
</script>

<div class="relative border-solid border-b border-b-neutral-400 mx-0 mt-[30px] mb-[15px]">
	{#if !showPassword}
		<input
			id={identifier}
			type="password"
			placeholder=" "
			bind:value
			on:input={hidePassError}
			required
			autocomplete="off"
			class={style}
		/>
	{:else}
		<input
			id={identifier}
			type="text"
			placeholder=" "
			bind:value
			on:input={hidePassError}
			required
			autocomplete="off"
			class={style}
		/>
	{/if}
	<label
		for={identifier}
		class="absolute top-1/2 left-[5px] text-neutral-400 -translate-y-1/2 pointer-events-none peer-focus:-translate-y-[35px] peer-focus:text-violet-600 peer-focus:font-medium transition-all duration-[.5s] peer-[&:not(:placeholder-shown)]:-translate-y-[35px] peer-[&:not(:placeholder-shown)]:text-violet-600 peer-[&:not(:placeholder-shown)]:font-medium"
		>{label}</label
	>

	<button
		type="button"
		on:click={toggleShowPassword}
		class="absolute top-1/2 right-[5px] -translate-y-1/2 h-8 w-8 border-none"
	>
		<img src={showPassword ? './hide.ico' : './show.ico'} alt={identifier} />
	</button>
</div>
