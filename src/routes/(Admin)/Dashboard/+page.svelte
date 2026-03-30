<script lang="ts">
	import SideBar from '../../(side-bar)/side-bar/side-bar.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import Plus from '@tabler/icons-svelte/icons/plus';
	import Certificate from '@tabler/icons-svelte/icons/certificate';
	import FileCertificate from '@tabler/icons-svelte/icons/file-certificate';
	import RosetteAsterisk from '@tabler/icons-svelte/icons/rosette-asterisk';
	import * as Table from '$lib/components/ui/table/index.js';

	let { children } = $props();

	const userName = $state<string>('Eviqt');

	const invoices = [
		{
			invoice: 'INV001',
			paymentStatus: 'Paid',
			totalAmount: '$250.00',
			paymentMethod: 'Credit Card'
		},
		{
			invoice: 'INV002',
			paymentStatus: 'Pending',
			totalAmount: '$150.00',
			paymentMethod: 'PayPal'
		},
		{
			invoice: 'INV003',
			paymentStatus: 'Unpaid',
			totalAmount: '$350.00',
			paymentMethod: 'Bank Transfer'
		},
		{
			invoice: 'INV004',
			paymentStatus: 'Paid',
			totalAmount: '$450.00',
			paymentMethod: 'Credit Card'
		},
		{
			invoice: 'INV005',
			paymentStatus: 'Paid',
			totalAmount: '$550.00',
			paymentMethod: 'PayPal'
		},
		{
			invoice: 'INV006',
			paymentStatus: 'Pending',
			totalAmount: '$200.00',
			paymentMethod: 'Bank Transfer'
		},
		{
			invoice: 'INV007',
			paymentStatus: 'Unpaid',
			totalAmount: '$300.00',
			paymentMethod: 'Credit Card'
		}
	];
</script>

<main class="relative">
	<SideBar>
		<section class="flex flex-col gap-5 p-2">
			<div class="flex items-center justify-center rounded-md border border-gray-100 p-5 shadow">
				<div>
					<h1 class="text-xl font-bold">Welcome, {userName}!</h1>
					<p class="text-[13px]">Here's your certificate management Dashboard.</p>
				</div>
				<Button class="ml-auto cursor-pointer bg-blue-500 hover:bg-blue-600  active:scale-95 "
					><Plus></Plus> create new certificate</Button
				>
			</div>
			<section class="grid grid-cols-3 gap-3">
				<div
					class="flex flex-row items-center justify-center rounded-lg border border-gray-300 p-5 shadow"
				>
					<div class="flex flex-col gap-2 p-5">
						<h1 class="text-sm">Total Created Certificates</h1>
						<div>
							<span class="text-2xl font-bold">1,000</span>
						</div>
					</div>
					<Certificate class="ml-auto size-15 rounded-full bg-blue-400 p-1"></Certificate>
				</div>
				<div
					class="flex flex-row items-center justify-center rounded-lg border border-gray-300 p-5 shadow"
				>
					<div class="flex flex-col gap-1 p-5">
						<h1 class="text-sm">Certificates Issued Today</h1>
						<div>
							<span class="text-2xl font-bold">30</span>
						</div>
					</div>
					<FileCertificate class="ml-auto size-15 rounded-full bg-green-400 p-1 "></FileCertificate>
				</div>
				<div
					class="flex flex-row items-center justify-center rounded-lg border border-gray-300 p-5 shadow"
				>
					<div class="flex flex-col gap-1 p-5">
						<h1 class="text-sm">New Request</h1>
						<div>
							<span class="text-2xl font-bold">2</span>
						</div>
					</div>
					<RosetteAsterisk class="ml-auto size-15 rounded-full bg-yellow-400 p-1"></RosetteAsterisk>
				</div>
			</section>
			<div>
				<h1>Recent Certificate Activity</h1>
				<p>Latest issued certificates</p>
			</div>
			<Table.Root>
				<Table.Caption>A list of your recent invoices.</Table.Caption>
				<Table.Header>
					<Table.Row>
						<Table.Head class="w-[100px]">LRN</Table.Head>
						<Table.Head>NAME</Table.Head>
						<Table.Head>DATE ISSUED</Table.Head>
						<Table.Head class="text-end">Amount</Table.Head>
					</Table.Row>
				</Table.Header>
				<Table.Body>
					{#each invoices as invoice (invoice)}
						<Table.Row>
							<Table.Cell class="font-medium">{invoice.invoice}</Table.Cell>
							<Table.Cell>{invoice.paymentStatus}</Table.Cell>
							<Table.Cell>{invoice.paymentMethod}</Table.Cell>
							<Table.Cell class="text-end">{invoice.totalAmount}</Table.Cell>
						</Table.Row>
					{/each}
				</Table.Body>
				<Table.Footer>
					<Table.Row>
						<Table.Cell colspan={3}>Total</Table.Cell>
						<Table.Cell class="text-end">$2,500.00</Table.Cell>
					</Table.Row>
				</Table.Footer>
			</Table.Root>
			{@render children?.()}
		</section>
	</SideBar>
</main>
