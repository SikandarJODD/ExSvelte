<!-- Simple Dark -->
<script>
	import { page } from '$app/stores';
	import ToggleTheme from '$lib/features/darkMode/ToggleTheme.svelte';
	import { slide } from 'svelte/transition';
	let nav = {
		title: 'Svelte Tailwinds',
		img: 'https://cdn-icons-png.flaticon.com/512/5769/5769490.png',
		listnavs: [
			{
				name: 'Home',
				link: '/'
			},
			{
				name: 'Interview',
				link: '/interview'
			},
			{
				name: 'Animations',
				link: '/animations'
			},
			{
				name: 'About',
				link: '/about'
			}
		]
	};

	$: isActive = $page.route.id;

	let isProfileMenu = false;
	let isMobileMenu = false;
</script>

<nav class="sticky z-40 bg-gray-900 md:top-4 md:bg-transparent">
	<div
		class="mx-auto w-full border-gray-800 {isMobileMenu
			? 'border-b border-slate-300'
			: ''} px-4 backdrop-blur-sm sm:px-6 md:w-fit md:rounded-full md:border md:shadow-md lg:px-2"
	>
		<div class="flex h-14 items-center justify-between sm:justify-center">
			<div class="">
				<a href="/" class="flex-shrink-0 text-xl font-semibold text-primary sm:hidden"
					>Svelte Learnings</a
				>
				<!-- Change Justify-center to end, start -->
				<div class="hidden w-full justify-center sm:flex">
					<div class="flex items-center space-x-3">
						{#each nav.listnavs as item}
							<a
								href={item.link}
								class="{isActive === item.link
									? 'bg-gray-800 text-slate-50 '
									: 'border  border-transparent text-gray-700 transition-all duration-150 hover:border hover:border-primary hover:text-primary  dark:text-primary'}   rounded-full px-4 py-2 text-sm font-medium transition-all duration-150 md:px-5 md:py-2.5"
								>{item.name}</a
							>
						{/each}
						<ToggleTheme />
					</div>
				</div>
			</div>

			<div class="-mr-2 flex sm:hidden">
				<!-- Mobile menu button -->
				<button
					type="button"
					class="relative inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
					aria-controls="mobile-menu"
					aria-expanded="false"
					on:click={() => (isMobileMenu = !isMobileMenu)}
				>
					<span class="absolute -inset-0.5" />
					<span class="sr-only">Open main menu</span>
					<!--
                Icon when menu is closed.
    
                Menu open: "hidden", Menu closed: "block"
              -->
					<svg
						class="{isMobileMenu ? 'hidden' : 'block'}  h-6 w-6"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="1.5"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
						/>
					</svg>

					<svg
						class="{isMobileMenu ? 'block' : 'hidden'}  h-6 w-6"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="1.5"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
					</svg>
				</button>
			</div>
		</div>
	</div>

	<!-- Mobile menu, show/hide based on menu state. -->
	{#key isMobileMenu}
		<div
			class="sm:hidden {isMobileMenu ? 'block' : 'hidden'}"
			id="mobile-menu"
			in:slide={{ duration: 300, delay: 50 }}
			out:slide={{ duration: 300 }}
		>
			<div class="space-y-1 px-2 pb-3 pt-2">
				<!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
				{#each nav.listnavs as item}
					<a
						on:click={() => (isMobileMenu = !isMobileMenu)}
						href={item.link}
						class="{isActive === item.link
							? 'bg-gray-900 text-white'
							: 'text-gray-300 hover:bg-gray-700 hover:text-white'}  block rounded-md px-3 py-2 text-base font-medium"
						>{item.name}</a
					>
				{/each}
				<div>
					<!-- Dark Mode / Light Mode -->
					<ToggleTheme />
				</div>
			</div>
		</div>
	{/key}
</nav>
