<script lang="ts">
	import { onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';
	import { cubicOut } from 'svelte/easing';
	import * as Card from '$lib/components/ui/card';
	import { Badge } from '$lib/components/ui/badge';
	import ExternalLinkIcon from '@lucide/svelte/icons/external-link';
	import ZoomIn from '@lucide/svelte/icons/zoom-in';
	import X from '@lucide/svelte/icons/x';
	import * as Carousel from '$lib/components/ui/carousel';

	import * as omiraTechImages from '$lib/assets/projects/omira-tech/index';
	import * as showBoxImages from '$lib/assets/projects/show-box/index';
	import * as portfolioImages from '$lib/assets/projects/portfolio/index';
	import InteractiveHoverButton from '$lib/components/magic/interactive-hover-button/interactive-hover-button.svelte';
	import SimpleIcon from '$lib/components/simple-icon.svelte';
	import { Button } from '$lib/components/ui/button';
	let mounted = $state(false);
	let zoomedProject = $state<(typeof projects)[0] | null>(null);

	const projects = [
		{
			id: 'Portfolio',
			name: 'Portfolio',
			description:
				"A modern developer's portfolio to showcase projects, skills, and experience — featuring a clean UI and responsive design",
			images: [
				portfolioImages.image1,
				portfolioImages.image2,
				
			],
			tech: [ 'Svelte', 'TypeScript', 'Tailwind CSS', 'Vercel', 'Pnpm'],
			link: 'https://vaultsy.vercel.app',
			github: 'https://github.com/Ayushkumar48/vaultsy',
			showSite: true
		},
		{
			id: 'Omira-Tech',
			name: 'Omira-Tech',
			description:
				'Your one stop go to for all your Tech. The perfect E-commerce Website',
			images: [
				omiraTechImages.image1,
				omiraTechImages.image2,
				omiraTechImages.image3,
				omiraTechImages.image4,

			],
			tech: ['Svelte', 'TypeScript', 'Tailwind CSS', 'MongoDB'],
			link: 'https://roast-me-kit.vercel.app',
			github: 'https://github.com/ayushkumar48/roast-me',
			showSite: true
		},
		{
			id: 'Show-Box',
			name: 'Show-Box',
			description: "Your college's private repository for showcasing student and faculty projects, fostering collaboration within our academic community.",
			images: [
				showBoxImages.image1,
				showBoxImages.image2,
				showBoxImages.image3,
				showBoxImages.image4,
				showBoxImages.image5,
			],
			tech: ['Svelte', 'TypeScript', 'Tailwind CSS', 'Drizzle', 'PostgreSQL', 'AWS S3',],
			link: 'https://showboxvit.vercel.app/',
			github: 'https://github.com/Yuvii2003/ShowBox'
		},
	];

	onMount(() => {
		mounted = true;
	});
</script>

<div
	class="relative overflow-x-hidden bg-background bg-[radial-gradient(circle,color-mix(in_oklch,var(--foreground)_45%,transparent)_1px,transparent_1px)] bg-size-[20px_20px] px-3 py-24 font-['Inter'] sm:px-4 md:px-6 md:py-12 lg:px-8 xl:px-12"
>
	<div class="mx-auto mb-12 w-full max-w-7xl sm:mb-16 md:mb-20">
		{#if mounted}
			<div
				class="relative mb-10 text-center sm:mb-14 md:mb-20"
				in:fade={{ duration: 800, easing: cubicOut }}
			>
				<h1
					class="mb-3 bg-linear-to-r from-primary via-chart-1 to-chart-4 bg-clip-text font-['Anton'] text-3xl text-transparent sm:text-4xl md:text-6xl lg:text-7xl xl:text-8xl"
				>
					PROJECTS
				</h1>
				<p
					class="mx-auto max-w-2xl px-2 font-['Anton'] text-xs text-muted-foreground sm:text-sm md:text-lg lg:text-xl"
				>
					A showcase of innovative applications built with cutting-edge technologies, solving
					real-world problems
				</p>
			</div>
		{/if}

		<div class="grid grid-cols-1 gap-4 sm:grid-cols-2 sm:gap-5 md:gap-6 lg:grid-cols-3 lg:gap-8">
			{#each projects as project, i (project.id)}
				{#if mounted}
					<div
						in:fly={{ y: 50, duration: 600, delay: i * 100, easing: cubicOut }}
						class="group h-full"
					>
						<Card.Root class="flex h-full flex-col bg-background">
							<div
								class="absolute inset-0 -z-10 bg-linear-to-br from-transparent via-transparent opacity-0 transition-opacity duration-500 group-hover:opacity-100"
								style="background: linear-gradient(135deg, transparent 0%, rgba(255, 62, 0, 0.1) 100%);"
							></div>

							<div class="overflow-hidden rounded-t-lg">
								<Carousel.Root class="w-full">
									<Carousel.Content>
										{#each project.images as image, j (j)}
											<Carousel.Item>
												<button
													type="button"
													class="group/zoom relative h-32 w-full sm:h-40 md:h-48"
													onclick={() => {
														zoomedProject = project;
													}}
													aria-label="Zoom image"
												>
													<enhanced:img
														src={image}
														alt="{project.name} screenshot {j + 1}"
														class="h-full w-full cursor-zoom-in object-cover"
													/>
													<div
														class="absolute inset-0 flex items-center justify-center bg-black/0 transition-colors duration-200 group-hover/zoom:bg-black/20"
													>
														<ZoomIn
															class="h-5 w-5 text-white opacity-0 transition-opacity duration-200 group-hover/zoom:opacity-100"
														/>
													</div>
												</button>
											</Carousel.Item>
										{/each}
									</Carousel.Content>
									{#if project.images.length > 1}
										<Carousel.Previous
											class="left-1 h-5 w-5 opacity-0 transition-opacity duration-200 group-hover:opacity-100 sm:left-2 sm:h-6 sm:w-6 md:h-7 md:w-7"
										/>
										<Carousel.Next
											class="right-1 h-5 w-5 opacity-0 transition-opacity duration-200 group-hover:opacity-100 sm:right-2 sm:h-6 sm:w-6 md:h-7 md:w-7"
										/>
									{/if}
								</Carousel.Root>
							</div>

							<Card.Header class="p-3 sm:p-4 md:p-6">
								<Card.Title class="text-base sm:text-lg md:text-xl">{project.name}</Card.Title>
								<Card.Description class="text-xs sm:text-sm md:text-base"
									>{project.description}</Card.Description
								>
							</Card.Header>

							<Card.Content class="flex flex-1 flex-col px-3 py-2 sm:px-4 sm:py-3 md:px-6 md:py-4">
								<div class="mb-auto"></div>
								<div class="flex flex-wrap gap-1.5 sm:gap-2">
									{#each project.tech as tech (tech)}
										<Badge variant="secondary" class="text-xs sm:text-xs md:text-sm">
											{tech}
										</Badge>
									{/each}
								</div>
							</Card.Content>

							<Card.Footer
								class="flex flex-col gap-2 px-3 py-3 sm:flex-row sm:gap-2 sm:px-4 sm:py-4 md:gap-3 md:px-6 md:py-4"
							>
								{#if project.link}
									<InteractiveHoverButton
										href={project.link}
										target="_blank"
										class="w-full text-xs sm:text-sm"
										useWindow
									>
										{#if project.showSite}
											Visit Site
										{:else}
											View Demo
										{/if}
										{#snippet icon()}
											<ExternalLinkIcon class="h-3 w-3 sm:h-4 sm:w-4" />
										{/snippet}
									</InteractiveHoverButton>
								{/if}
								<InteractiveHoverButton
									href={project.github}
									target="_blank"
									class="w-full text-xs sm:text-sm"
									useWindow
								>
									GitHub
									{#snippet icon()}
										<SimpleIcon name="github" size="h-3 w-3 sm:h-4 sm:w-4" />
									{/snippet}
								</InteractiveHoverButton>
							</Card.Footer>
						</Card.Root>
					</div>
				{/if}
			{/each}
		</div>
	</div>
</div>

{#if zoomedProject}
	<div
		class="fixed inset-0 z-50"
		role="dialog"
		aria-modal="true"
		transition:fly={{ y: -100, duration: 600, easing: cubicOut }}
	>
		<Button
			onclick={() => (zoomedProject = null)}
			variant="outline"
			class="absolute top-4 right-4 z-10 text-white transition-colors hover:text-gray-300"
			aria-label="Close zoom"
			type="button"
		>
			<X class="h-8 w-8" />
		</Button>

		<div class="h-screen w-screen">
			<Carousel.Root class="h-full w-full">
				<Carousel.Content class="h-full">
					{#each zoomedProject.images as image, j (j)}
						<Carousel.Item class="h-full basis-full">
							<div class="flex h-full w-full items-center justify-center">
								<enhanced:img
									src={image}
									alt="{zoomedProject.name} screenshot {j + 1}"
									class="h-full w-full object-contain"
								/>
							</div>
						</Carousel.Item>
					{/each}
				</Carousel.Content>
				{#if zoomedProject.images.length > 1}
					<Carousel.Previous class="left-6 h-10 w-10 text-white hover:text-gray-300" />
					<Carousel.Next class="right-6 h-10 w-10 text-white hover:text-gray-300" />
				{/if}
			</Carousel.Root>
		</div>
	</div>
{/if}