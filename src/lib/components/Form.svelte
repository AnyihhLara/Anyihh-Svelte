<script lang="ts">
	import Header from './Header.svelte';
	import SubmitButton from './SubmitButton.svelte';
</script>

<form
	autocomplete="off"
	on:submit|preventDefault
	class="flex flex-col justify-between bg-white w-[400px] rounded-[10px]"
>
	<div class="px-10 py-5">
		<Header>
			<slot name="header" />
		</Header>
	</div>
	<hr />
	<div class="px-10">
		<slot />
	</div>
	<div class="px-10">
		<slot name="footer">
			<SubmitButton>
				<slot name="submit-btn-text" />
			</SubmitButton>
		</slot>
	</div>
</form>
