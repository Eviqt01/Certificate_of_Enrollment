<script lang="ts">
	import SideBar from '../../(side-bar)/side-bar/side-bar.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import Plus from '@tabler/icons-svelte/icons/plus';
	import Certificate from '@tabler/icons-svelte/icons/certificate';

	const userName = $state<string>('Eviqt');
</script>

<main class="flex">
	<SideBar></SideBar>
	<section class="flex w-full flex-col gap-5 p-5">
		<div
			class="flex max-w-screen items-center justify-center self-start rounded-md border border-gray-100 p-5 shadow"
		>
			<div>
				<h1 class="text-xl font-bold">Welcome, {userName}</h1>
				<p class="text-[13px]">Here's your certificate management Dashboard.</p>
			</div>
			<Button class="cursor-pointers ml-auto bg-blue-500  hover:bg-blue-600 "
				><Plus></Plus> create new certificate</Button
			>
		</div>
		<section class="grid grid-cols-3 items-center justify-around gap-3">
			<div class="flex flex-row items-center border border-gray-300 p-5 shadow">
				<div class="flex flex-col gap-1 p-5">
					<h1 class="text-xs">Total Created Certificates</h1>
					<div>
						<span class="text-2xl font-bold">1,000</span>
						<p class="text-sm text-green-500">↑ 12% from last month</p>
					</div>
				</div>
				<Certificate></Certificate>
			</div>
			<div class="flex flex-row items-center border border-gray-300 p-5 shadow">
				<div class="flex flex-col gap-1 p-5">
					<h1 class="text-xs">Total Created Certificates</h1>
					<div>
						<span class="text-2xl font-bold">1,000</span>
						<p class="text-sm text-green-500">↑ 12% from last month</p>
					</div>
				</div>
				<Certificate></Certificate>
			</div>
			<div class="flex flex-row items-center border border-gray-300 p-5 shadow">
				<div class="flex flex-col gap-1 p-5">
					<h1 class="text-xs">Total Created Certificates</h1>
					<div>
						<span class="text-2xl font-bold">1,000</span>
						<p class="text-sm text-green-500">↑ 12% from last month</p>
					</div>
				</div>
				<Certificate></Certificate>
			</div>
		</section>
	</section>
</main>
