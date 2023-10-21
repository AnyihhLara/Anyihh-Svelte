<script>
	import Form from '$lib/components/Form.svelte';
	import InputText from '$lib/components/Inputs/InputText.svelte';
	import InputPassword from '../lib/components/Inputs/InputPassword.svelte';

	let valid = false;
	let confirmPassword = '';
	let user = {
		name: '',
		password: ''
	};
	let userValidation = {
		valid: true,
		message: ''
	};
	let confirmPasswordValidation = {
		valid: true,
		message: ''
	};

	const validate = () => {
		const userValid = localStorage.getItem(user.name) === null; //cool quick-test database xd
		const passValid = user.password === confirmPassword;
		setValidity({ userValid, passValid });
		if (valid) {
			localStorage.setItem(user.name, JSON.stringify(user));
		}
	};
	const setValidity = ({ userValid, passValid }) => {
		valid = userValid && passValid;
		setTimeout(() => (valid = false), 5000);
		if (!userValid) {
			userValidation.message = 'Este usuario ya existe.';
			userValidation.valid = false;
			setTimeout(() => (userValidation = { message: '', valid: true }), 5000);
		}
		if (!passValid) {
			confirmPasswordValidation.message = 'Las contraseñas deben ser iguales.';
			confirmPasswordValidation.valid = false;
			setTimeout(() => (confirmPasswordValidation = { message: '', valid: true }), 5000);
		}
	};
	const hideUserError = () => {
		userValidation = {
			valid: true,
			message: ''
		};
	};
	const hidePassError = () => {
		confirmPasswordValidation = {
			valid: true,
			message: ''
		};
	};
</script>

<Form on:submit={validate}>
	<svelte:fragment slot="header">Registrar Cuenta</svelte:fragment>
	<InputText
		id="username"
		required
		bind:value={user.name}
		on:input={hideUserError}
		bind:validation={userValidation}
	>
		Nombre de Usuario
	</InputText>
	<InputPassword id="password" bind:value={user.password} on:input={hidePassError}>
		Contraseña
	</InputPassword>
	<InputPassword
		id="password-confirm"
		bind:value={confirmPassword}
		on:input={hidePassError}
		bind:validation={confirmPasswordValidation}
	>
		Confirmar Contraseña
	</InputPassword>
	<svelte:fragment slot="submit-btn-text">Registrarse</svelte:fragment>
	{#if valid}
		<div class="text-center pb-5">
			<span class="text-violet-700 font-medium">Se ha registrado con éxito.</span>
		</div>
	{/if}
</Form>
