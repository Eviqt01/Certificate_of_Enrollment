<script lang="ts">
	import Label from '$lib/components/ui/label/label.svelte';
	import Input from '$lib/components/ui/input/input.svelte';
	import RizalIcon from '../../images/rizalIcon.jpeg';
	import Josol from '../../images/Josol.jpg';
	import IconBook from '@tabler/icons-svelte/icons/book';
	import User from '@tabler/icons-svelte/icons/user';
	import Key from '@tabler/icons-svelte/icons/key';
	import IconEye from '@tabler/icons-svelte/icons/eye';
	import IconEyeOff from '@tabler/icons-svelte/icons/eye-off';
	import Checkbox from '$lib/components/ui/checkbox/checkbox.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';

	let rememberMe = $state(false);
	let emailInput = $state<string>('');
	let passwordInput = $state<string>('');

	onMount(() => {
		rememberMe = localStorage.getItem('rememberMe') === 'true';
		emailInput = localStorage.getItem('savedEmail') ?? '';
		passwordInput = localStorage.getItem('savedPassword') ?? '';
	});

	let showPassword = $state(false);
	let passwordType = $derived(showPassword ? 'text' : 'password');

	const togglePassword = () => {
		showPassword = !showPassword;
	};

	let warningMessage = $state<string>('');
	const userEmail = $state<string>('josol123@gmail.com');
	const userPassword = $state<string>('josol123');

	const credentialsValidation = () => {
		if (rememberMe) {
			localStorage.setItem('rememberMe', 'true');
			localStorage.setItem('savedEmail', emailInput);
			localStorage.setItem('savedPassword', passwordInput);
		} else {
			localStorage.removeItem('rememberMe');
			localStorage.removeItem('savedEmail');
			localStorage.removeItem('savedPassword');
		}
		const invalidCharacters = /[$=!+\-#%^&*()]/;
		if (emailInput === userEmail && passwordInput === userPassword) {
			goto('/Dashboard');
		} else {
			warningMessage = 'Please Enter a Valid Credentials';
		}
		if (invalidCharacters.test(emailInput)) {
			warningMessage = 'Special Characters is not Allowed, Except @.';
		} else if (emailInput === '') {
			warningMessage = "Please Don't leave it blank.";
		} else if (!emailInput.includes('@')) {
			warningMessage = 'Please Enter Correct Email.';
		}
	};
</script>

<main class="relative flex min-h-screen items-center justify-center">
	<section
		class="relative z-10 flex min-h-screen w-full flex-col items-center justify-center gap-2"
	>
		<img
			src={Josol}
			class="absolute top-0 z-1 min-h-screen bg-center bg-no-repeat"
			alt="JosolPic"
		/>
		<img src={RizalIcon} class="z-20 size-25 rounded-full" alt="rizalicon" />
		<div class="relative z-20 flex flex-col items-center gap-2 font-sans text-white">
			<div class=" flex items-center gap-2">
				<IconBook
					class="size-12 rounded-xl border border-white/30   bg-white/20 p-2 backdrop-blur-none"
				></IconBook>
				<h1 class="text-2xl font-bold">Rizal High School</h1>
			</div>
			<p class="text-lg">Registrar Office's Certificate of Enrollment</p>
			<p class="text-xs">
				Simplify the process of obtaining your Certificate of Enrollment with our platform.
			</p>
		</div>
	</section>
	<section class=" flex min-h-screen w-full items-center justify-center p-10">
		<form
			class="flex w-120 max-w-screen flex-col gap-5 rounded-md border border-white/40 p-5 shadow"
		>
			<div class="flex flex-col items-center gap-1">
				<h1 class="font-sans text-3xl font-bold">Sign In to Registrar</h1>
				<p class="font-sans text-sm">Enter your credentials to access the dashboard</p>
			</div>
			<div class="flex flex-col gap-2">
				<Label for="email" class="font-sans">Email</Label>
				<div class="flex items-center">
					<User class="absolute z-1 ml-2 size-5"></User>
					<Input
						type="email"
						class="rounded-lg px-9"
						name="email"
						placeholder="Enter your Credentials"
						bind:value={emailInput}
					/>
				</div>
			</div>

			<div class="flex flex-col gap-2">
				<Label for="password" class="font-sans">Password</Label>
				<div class="flex items-center">
					<Key class="absolute z-1 ml-2 size-5"></Key>
					<Input
						type={passwordType}
						class="rounded-lg px-9"
						name="email"
						placeholder="Enter your Credentials"
						bind:value={passwordInput}
					/>
				</div>
				{#if showPassword}
					<button class="absolute z-10 mt-7 mr-3 self-end" onclick={togglePassword}
						><IconEye></IconEye></button
					>
				{:else}
					<button class="absolute z-10 mt-7 mr-3 self-end" onclick={togglePassword}
						><IconEyeOff></IconEyeOff></button
					>
				{/if}
			</div>
			<div class="relative flex items-center justify-center">
				<div class="flex items-center gap-1">
					<Checkbox name="rememberMe" bind:checked={rememberMe}></Checkbox>

					<Label for="rememberMe">Remember Me</Label>
				</div>
				<a
					href="#"
					class="ml-auto border-b border-transparent text-sm font-bold text-blue-500 hover:border-b hover:border-blue-500"
					>Forgot Password?</a
				>
			</div>

			<Button
				class="cursor-pointer rounded-lg bg-blue-500 hover:bg-blue-700 active:scale-[0.95]"
				onclick={credentialsValidation}>Sign In</Button
			>
			<h1 class="text-center text-xs">
				Certificate of Enrollment • <a href="#" class="text-blue-500 hover:underline"
					>Terms of Services</a
				>
			</h1>
			<span class="text-center text-xs text-red-500">{warningMessage}</span>
		</form>
	</section>
</main>
