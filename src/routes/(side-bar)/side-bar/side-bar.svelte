<script lang="ts">
	import Layout2 from '@tabler/icons-svelte/icons/layout-2';
	import FileAnalytics from '@tabler/icons-svelte/icons/file-analytics';
	import Archive from '@tabler/icons-svelte/icons/archive';
	import Settings from '@tabler/icons-svelte/icons/settings';
	import RizalIcon from '../../images/rizalIcon.jpeg';
	import Point from '@tabler/icons-svelte/icons/point';

	const sideBarItems = [
		{
			label: 'Home',
			href: '/Dashboard',
			icons: Layout2
		},
		{
			label: 'Create Certificate',
			href: '/create-certificate',
			icons: FileAnalytics
		},
		{
			label: 'Records Vault',
			href: '/records-vault',
			icons: Archive
		},
		{
			label: 'Settings',
			href: '/settings',
			icons: Settings
		}
	];
</script>

<nav class="relative left-0 z-10">
	<ul
		class="flex min-h-screen w-150 max-w-[220px] flex-col justify-center gap-2 bg-gray-700 px-1 py-4"
	>
		<section class="ml-2 flex items-center gap-2 py-2">
			<img src={RizalIcon} class="size-10 rounded-full" alt="rizalicon" />
			<div class="flex flex-col gap-1">
				<h1 class="text-xs text-gray-300">Certificate of Enrollment</h1>
				<h1 class="font-sans font-bold text-white">Rizal High School</h1>
			</div>
		</section>
		<hr class="border border-gray-500" />
		{#each sideBarItems as sidebarItems (sidebarItems.label)}
			<li
				class="active:scale[0.95] flex flex-row items-center gap-1 rounded-md text-white hover:bg-gray-500"
			>
				<sidebarItems.icons class="ml-2 size-6" /><a href={sidebarItems.href} class="py-2 text-sm"
					>{sidebarItems.label}</a
				>
			</li>
		{/each}
		<section
			class="mt-auto flex flex-row items-center justify-center rounded-md bg-gray-600 px-5 py-2"
		>
			<div class="mr-auto flex flex-col gap-2">
				<h1 class="text-xs text-gray-400">SYSTEM STATUS</h1>
				<div class="flex flex-col">
					<h1 class="text-xs text-white">Certificates</h1>
					<span class="text-lg text-white">0</span>
				</div>
			</div>
			<div
				class="full flex flex-row items-center rounded-md border border-green-400 px-2 py-1 text-green-500"
			>
				<Point class="size-4 "></Point>
				<h1 class="text-xs">Active</h1>
			</div>
		</section>
	</ul>
</nav>
