<script>
	import Icons from '../Icons.svelte';
	import dashboardItemList from '../itemList';
</script>

<div class="hidden md:fixed md:inset-y-0 md:flex md:w-64 md:flex-col">
	<div class="flex min-h-0 flex-1 flex-col bg-gray-800">
		<div class="flex h-16 flex-shrink-0 items-center bg-gray-900 px-4">
			<img
				class="h-8 w-auto"
				src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500"
				alt="Your Company"
			/>
		</div>
		<div class="flex flex-1 flex-col overflow-y-auto">
			<nav class="flex-1 space-y-1 px-2 py-4">
				{#each dashboardItemList as item (item.id)}
					<a
						href="{item.href}"
						class="text-gray-300 hover:bg-gray-700 hover:text-white group flex items-center px-2 py-2 text-sm font-medium rounded-md"
					>
						<Icons name="{item.name}" />
						{item.name}
					</a>
				{/each}
			</nav>
		</div>
	</div>
</div>
