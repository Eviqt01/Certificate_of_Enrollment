<script lang="ts">
	import About from './(nav-bar)/About/about.svelte';
	import Help from './(nav-bar)/Help/help.svelte';
	import Contact from './(nav-bar)/Contact/contact.svelte';
	import Login from '.././routes/(auth)/login/+page.svelte';
	import RizalIcon from '../routes/images/rizalIcon.jpeg';
	import SunIcon from '@lucide/svelte/icons/sun';
	import MoonIcon from '@lucide/svelte/icons/moon';
	import { toggleMode } from 'mode-watcher';
	import { Button } from '$lib/components/ui/button/index.js';
	import { ModeWatcher } from 'mode-watcher';

	let { children } = $props();

	const navBar = [
		{
			label: 'Home',
			href: '/'
		},
		{
			label: 'About',
			href: '#About'
		},
		{
			label: 'Help',
			href: '#Help'
		},
		{
			label: 'Contact',
			href: '#Contact'
		}
	];
</script>

<nav class="sticky top-0 z-30 flex items-center justify-center border border-white/2 p-2 shadow-md">
	<section class="flex flex-row items-center gap-2">
		<img src={RizalIcon} class="size-10" alt="rizalIcon" />
		<div class="flex flex-col">
			<h1>Rizal High School</h1>
			<p class="text-sm">Certificate of Enrollment</p>
		</div>
	</section>
	<ul class="ml-auto flex gap-5 px-5 text-lg">
		<Button onclick={toggleMode} variant="outline" size="icon">
			<SunIcon
				class="h-[1.2rem] w-[1.2rem] scale-100 rotate-0 transition-all! dark:scale-0 dark:-rotate-90"
			/>
			<MoonIcon
				class="absolute h-[1.2rem] w-[1.2rem] scale-0 rotate-90 transition-all! dark:scale-100 dark:rotate-0"
			/>
			<span class="sr-only">Toggle theme</span>
		</Button>
		<ModeWatcher />
		{@render children?.()}
		{#each navBar as navbar (navbar.label)}
			<li>
				<a href={navbar.href} class="active:scale[0.95] p-2 hover:rounded-md hover:bg-gray-300"
					>{navbar.label}</a
				>
			</li>
		{/each}
	</ul>
</nav>
<Login></Login>
<About></About>
<Help></Help>
<Contact></Contact>
<footer></footer>
