<script lang="ts">
	export let forID;
</script>

<label
	for={forID}
	class="absolute top-1/2 left-[5px] text-neutral-400 -translate-y-1/2 pointer-events-none peer-focus:-translate-y-[35px] peer-focus:text-violet-600 peer-focus:font-medium transition-all duration-[.5s] peer-[&:not(:placeholder-shown)]:-translate-y-[35px] peer-[&:not(:placeholder-shown)]:text-violet-600 peer-[&:not(:placeholder-shown)]:font-medium"
>
	<slot />
</label>
