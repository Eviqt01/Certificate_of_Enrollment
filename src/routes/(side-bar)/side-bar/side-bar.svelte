<script lang="ts">
	import Layout2 from '@tabler/icons-svelte/icons/layout-2';
	import FileAnalytics from '@tabler/icons-svelte/icons/file-analytics';
	import Archive from '@tabler/icons-svelte/icons/archive';
	import Settings from '@tabler/icons-svelte/icons/settings';
	import Logs from '@tabler/icons-svelte/icons/logs';
	import * as Sidebar from '$lib/components/ui/sidebar/index.js';
	import AppSidebar from '$lib/components/app-sidebar.svelte';

	let { children } = $props();

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
			icons: Logs
		},
		{
			label: 'Settings',
			href: '/settings',
			icons: Settings
		},
		{
			label: 'Archive',
			href: '/archive',
			icons: Archive
		}
	];
</script>

<Sidebar.Provider>
	<AppSidebar />
	<Sidebar.Trigger />

	<main class="relative w-full">
		{@render children?.()}
		<Sidebar.Root>
			<Sidebar.Content>
				<Sidebar.Group>
					<Sidebar.GroupLabel>Application</Sidebar.GroupLabel>
					<Sidebar.GroupContent>
						<Sidebar.Menu>
							{#each sideBarItems as sidebarItems (sidebarItems.label)}
								<Sidebar.MenuItem>
									<Sidebar.MenuButton>
										{#snippet child({ props })}
											<a href={sidebarItems.href} {...props}>
												<sidebarItems.icons />
												<span>{sidebarItems.label}</span>
											</a>
										{/snippet}
									</Sidebar.MenuButton>
								</Sidebar.MenuItem>
							{/each}
						</Sidebar.Menu>
					</Sidebar.GroupContent>
				</Sidebar.Group>
			</Sidebar.Content>
		</Sidebar.Root>
	</main>
</Sidebar.Provider>
