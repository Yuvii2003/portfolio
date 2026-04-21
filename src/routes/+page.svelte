<script lang="ts">
	import LineShadowText from '$lib/components/magic/line-shadow-text/line-shadow-text.svelte';
	import LightRays from '$lib/components/magic/light-rays/light-rays.svelte';
</script>

<div class="relative min-h-screen w-full overflow-hidden py-16 pb-24! sm:py-14 md:py-10">
	<LightRays count={5} blur={40} />
	<div
		class="flex min-h-screen w-full flex-col items-center justify-center px-4 py-6 md:px-8 lg:px-10"
	>
		<div
			class="flex w-full max-w-4xl flex-col gap-6 rounded-xl bg-accent/80 px-4 py-6 text-accent-foreground backdrop-blur-sm sm:gap-8 sm:rounded-2xl sm:px-6 sm:py-8 md:gap-10 md:px-8"
		>
			<h2
				class="text-center text-5xl leading-tight font-extrabold sm:text-7xl md:text-8xl xl:text-9xl"
			>
				Frontend <LineShadowText content="Dev" shadowColor="var(--primary-foreground)" />
			</h2>

			<div class="w-full">
				<p class="w-4/5 text-sm leading-relaxed sm:w-3/5 sm:text-base md:w-2/5 md:text-lg">
					I turn ideas into interactive, visually engaging experiences. From smooth animations to responsive layouts, I build frontend systems that don’t just work — they feel right.
				</p>
			</div>
			<div class="flex w-full justify-end">
				<p
					class="w-4/5 text-right text-sm leading-relaxed sm:w-3/5 sm:text-base md:w-2/5 md:text-lg"
				>
					With a keen eye for usability and detail, I simplify complex concepts into intuitive interfaces that are easy to understand and effortless to use.
				</p>
			</div>
		</div>
		<div
			class="mt-6 w-full max-w-4xl rounded-xl border border-border bg-card/85 px-4 py-6 text-card-foreground shadow-lg backdrop-blur-sm sm:mt-8 sm:rounded-2xl sm:px-6 sm:py-8 md:mt-10 md:px-8"
		>
			<h3 class="text-2xl font-bold sm:text-3xl md:text-4xl">About Me</h3>
			<p class="mt-3 text-sm leading-relaxed text-muted-foreground sm:mt-4 sm:text-base md:text-lg">
				I'm Yuvraj Kewalramani, a Software Engineer with hands-on experience building
				scalable web applications, robust APIs, and data-driven platforms. I specialize in
				Svelte, Node.js, PostgreSQL, MongoDB, and modern web technologies. My passion for
				crafting impactful solutions is reflected in projects like Omira-tech, an e-commerce
				platform and Show Box, a private academic repository fostering collaboration. I'm dedicated to system design, performance optimization, lean architecture, and delivering applications that provide seamless user experiences and drive real community engagement.
			</p>
			<p class="mt-3 text-sm leading-relaxed text-muted-foreground sm:mt-4 sm:text-base md:text-lg">
				Throughout my career, I've had the opportunity to work across the full stack—from crafting
				responsive UIs with Next.js and SvelteKit to architecting secure backend services and
				real-time messaging systems. I graduated from VIT Bhopal with a degree in Computer Science,
				and since then, I've contributed to products that serve users daily. I believe in writing code that's not just functional, but maintainable, performant, and built with the
				end user in mind. Whether it's shaving off milliseconds from API response times or designing
				database schemas that scale, I'm always chasing that perfect balance between elegance and
				efficiency.
			</p>
		</div>
	</div>
</div>
