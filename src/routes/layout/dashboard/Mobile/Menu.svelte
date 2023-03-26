<script>
	import { mobileMenuActive } from '../../layout-stores';
	import MenuClose from './MenuClose.svelte';
	import Icons from '../Icons.svelte';
	import dashboardItemList from '../itemList';

	let isMenuActive = false;

	const unsubscribe = mobileMenuActive.subscribe((value) => {
		isMenuActive = value;
	});
</script>

<div class="relative z-40 md:hidden" class:hidden={!isMenuActive} role="dialog" aria-modal="true">
	<div class="fixed inset-0 bg-gray-600 bg-opacity-75" />

	<div class="fixed inset-0 z-40 flex">
		<div class="relative flex w-full max-w-xs flex-1 flex-col bg-gray-800 pt-5 pb-4">
			<MenuClose />

			<div class="flex flex-shrink-0 items-center px-4">
				<img
					class="h-8 w-auto"
					src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500"
					alt="Your Company"
				/>
			</div>
			<div class="mt-5 h-0 flex-1 overflow-y-auto">
				<nav class="space-y-1 px-2">
					{#each dashboardItemList as item (item.id)}
						<a
							href={item.href}
							on:click={() => mobileMenuActive.update((n) => false)}
							class="text-gray-300 hover:bg-gray-700 hover:text-white group flex items-center px-2 py-2 text-sm font-medium rounded-md"
						>
							<Icons name={item.name} />
							{item.name}
						</a>
					{/each}
				</nav>
			</div>
		</div>

		<div class="w-14 flex-shrink-0" aria-hidden="true">
			<!-- Dummy element to force sidebar to shrink to fit close icon -->
		</div>
	</div>
</div>

<style>
	.hidden {
		display: none;
	}
</style>
