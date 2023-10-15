<script>
	//Exports
	export let hideUserError;
	export let identifier;
	export let label;
	export let value;
</script>

<div class="relative border-solid border-b border-b-neutral-400 mx-0 mt-[30px] mb-[15px]">
	<input
		id={identifier}
		type="text"
		bind:value
		on:input={hideUserError}
		placeholder=" "
		required
		class="peer w-full py-0 px-[5px] h-10 border-none bg-none outline-none"
	/>
	<label
		for={identifier}
		class="absolute top-1/2 left-[5px] text-neutral-400 -translate-y-1/2 pointer-events-none peer-focus:-translate-y-[35px] peer-focus:text-violet-600 peer-focus:font-medium transition-all duration-[.5s] peer-[&:not(:placeholder-shown)]:-translate-y-[35px] peer-[&:not(:placeholder-shown)]:text-violet-600 peer-[&:not(:placeholder-shown)]:font-medium"
		>{label}</label
	>
</div>
