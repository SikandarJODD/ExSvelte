<script>
	import Button from '$lib/components/ui/button/button.svelte';
	import { CheckCircle, Code, Wand2 } from 'lucide-svelte';
</script>

<div class=" -mt-12 flex h-screen flex-col items-center justify-center px-3">
	<div class=" text-center">
		<h1 class="my-5 text-5xl font-bold">SvelteKit Learnings</h1>
		<p class="max-w-4xl text-xl">
			Learn svelte tricks, animations, effects,and many more inspired from Joy of Code & Whole
			Svelte Community
		</p>
	</div>
	<!-- Tablet & Laptop users -->
	<div class="hidden md:flex">
		<div class="parent mt-4">
			<a href="/examples" class="box box1 relative border border-primary font-mono">Examples</a>
			<a href="/animations" class="box box2 group relative border border-primary font-mono">
				Animations
				<div
					class=" absolute right-2 top-2 h-4 w-4 rounded-full border border-primary transition-all duration-150 group-hover:bg-green-400"
				></div>
			</a>
			<a href="/interview" class="box box3 group relative border border-primary font-mono">
				Interview Questions
				<div
					class=" absolute right-2 top-2 h-4 w-4 rounded-full border border-primary transition-all duration-150 group-hover:bg-green-400"
				></div>
			</a>
		</div>
	</div>
	<!-- Mobile Users -->
	<div class="mt-4 flex flex-wrap justify-center gap-y-2 md:hidden">
		<Button href="/examples" size="lg" class="w-full">
			<Code strokeWidth="1.4" size="18" class="mr-1.5" />
			Examples</Button
		>
		<Button href="/interview" size="lg" class="w-full">
			<CheckCircle strokeWidth="1.4" size="18" class="mr-1.5" />
			Interview Questions</Button
		>
		<Button href="/animations" size="lg" class="w-full">
			<Wand2 strokeWidth="1.4" size="18" class="mr-1.5" />
			Animations</Button
		>
	</div>
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap');
	p {
		font-family: 'Montserrat', sans-serif;
	}
	.box {
		display: flex;
		border-radius: 7px;
		text-align: center;
		align-items: center;
		justify-content: center;
		font-size: 1.4rem;
		font-weight: bold;
		padding: 10px;
	}
	.box1 {
		grid-area: 1 / 1 / 2 / 3;
	}
	.box2 {
		grid-area: 2 / 1 / 3 / 3;
	}
	.box3 {
		grid-area: 1 / 3 / 3 / 6;
	}
	.parent {
		display: grid;
		grid-template-columns: repeat(5, 120px);
		grid-template-rows: repeat(2, 120px);
		grid-gap: 10px;
	}
</style>
