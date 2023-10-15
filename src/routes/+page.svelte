<script>
	//Imports
	import Error from '../lib/Error.svelte';
	import Input from '../lib/Input.svelte';
	import PasswordInput from '../lib/PasswordInput.svelte';

	//Variables
	let user = {
		name: '',
		password: ''
	};
	let confirmPassword = '';

	let passValid = true;
	let userValid = true;
	let valid = false;

	let showPassword = false;
	let showConfirmedPassword = false;

	//Functions
	function validate(e) {
		e.preventDefault();

		userValid = localStorage.getItem(user.name) === null;
		passValid = user.password === confirmPassword;
		valid = false;

		if (userValid && passValid) {
			valid = true;
			localStorage.setItem(`${user.name}`, JSON.stringify(user));
		}
	}

	function hideUserError(e) {
		e.preventDefault();
		userValid = true;
		valid = false;
	}

	function hidePassError(e) {
		e.preventDefault();
		passValid = true;
		valid = false;
	}

	function toggleShowPassword(e) {
		e.preventDefault();

		showPassword = !showPassword;
	}

	function toggleShowConfirmedPassword(e) {
		e.preventDefault();

		showConfirmedPassword = !showConfirmedPassword;
	}
</script>

<body class="font-sans text-base bg-gradient-to-r from-violet-400 to-violet-300 h-screen">
	<div class="min-h-screen flex items-center justify-center">
		<main class="bg-white w-[400px] rounded-[10px]">
			
			<h1
				class="text-2xl font-semibold my-5 text-center pb-5 border-solid border-b-[1px] border-b-zinc-400"
			>
				Registrar Cuenta
			</h1>

			<form on:submit={validate} class="py-0 px-10 box-border">
				
				<Input
					identifier="nombreusuario"
					label="Nombre de Usuario"
					bind:value={user.name}
					{hideUserError}
				/>

				{#if !userValid}
					<Error message="Ese usuario ya existe." />
				{/if}

				<PasswordInput
					identifier="password"
					label="Contraseña"
					bind:value={user.password}
					{hidePassError}
					{toggleShowPassword}
					{showPassword}
				/>
				<PasswordInput
					identifier="confirmPassword"
					label="Confirmar Contraseña"
					bind:value={confirmPassword}
					{hidePassError}
					toggleShowPassword={toggleShowConfirmedPassword}
					showPassword={showConfirmedPassword}
				/>

				{#if !passValid}
					<Error message="Las contraseñas tienen que ser iguales." />
				{/if}

				<div>
					<input
						type="submit"
						value="Registrar"
						class="w-full h-[50px] px-[6px] py-px bg-violet-700 rounded-full text-lg font-semibold text-white cursor-pointer outline-none mb-5 mt-[15px] duration-[.5s] hover:bg-violet-500 hover:duration-[.5s]"
					/>
				</div>

				{#if valid}
					<div class="text-center pb-5">
						<span class="text-violet-700 font-medium">Se ha registrado con éxito.</span>
					</div>
				{/if}
			</form>
		</main>
	</div>
</body>
