<!-- <script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import { initSwiper } from '$lib/index.js';
	import arrowRight from '$lib/assets/arrow-right.svg';

	import pictoVisuel from '$lib/assets/slider/picto-visuel.svg';
	import pictoMoteur from '$lib/assets/slider/picto-moteur.svg';
	import pictoAuditif from '$lib/assets/slider/picto-auditif.svg';
	import pictoIntellectuelle from '$lib/assets/slider/picto-intellectuelle.svg';
	import pictoPsychique from '$lib/assets/slider/picto-psychique.svg';
	// import pictoAutistique from '$lib/assets/slider/picto-autistique.svg';

	const slides = [
		{
			title_first_part: 'Handicap',
			title_second_part: 'visuel',
			description: `Le champ du handicap visuel est extrêmement large. Il touche officiellement 1,3 million de personnes, dont 2 à 3% seulement de personnes non-voyantes.
            Certaines personnes ont une acuité visuelle extrêmement faible, ne distinguent pas les couleurs, ne voient pas sur les côtés ou devant elles, ne distinguent que les contrastes lumineux… Parmi elles, 7 à 8 000 personnes utilisent le Braille.`,
			list: [],
			image: '/slider/handicap-visuel.png',
			picto: pictoVisuel,
			link: {
				href: '/handicaps',
				title: 'Explorer le handicap'
			}
		},
		{
			title_first_part: 'Handicap',
			title_second_part: 'moteur',
			description: `Les personnes atteintes de handicap moteur peuvent être regroupées en 3 catégories :`,
			list: [
				'Celles qui se déplacent en fauteuil roulant',
				'Celles qui se déplacent à l’aide d’une canne, de béquilles ou d’un déambulateur',
				'Celles qui se déplacent sans aide à la marche, mais manquent d’endurance ou de force.'
			],
			image: '/slider/handicap-moteur.png',
			picto: pictoMoteur,
			link: {
				href: '/handicaps',
				title: 'Explorer le handicap'
			}
		},
		{
			title_first_part: 'Handicap',
			title_second_part: 'auditif',
			description: `Le handicap auditif regroupe les personnes malentendantes et sourdes. Il touche environ 6 millions de personnes en France.
            Certaines personnes ont une perte auditive légère, d'autres sont totalement sourdes. Les solutions d'accessibilité incluent la langue des signes, les sous-titres et les boucles magnétiques.`,
			list: [],
			image: '/slider/handicap-auditif.png',
			picto: pictoAuditif,
			link: {
				href: '/handicaps',
				title: 'Explorer le handicap'
			}
		},
		{
			title_first_part: 'Déficience',
			title_second_part: 'intellectuelle',
			description: `Les personnes atteintes de déficience intellectuelle ont un QI très inférieur à la moyenne. Elles sont officiellement 700 000 en France. Elles éprouvent des difficultés à mobiliser leur attention, maîtriser le calcul et le raisonnement, comprendre les informations et, par conséquent, à s’adapter ou se repérer dans un environnement inconnu.`,
			list: [],
			image: '/slider/deficience-intellectuelle.png',
			picto: pictoIntellectuelle,
			link: {
				href: '/handicaps',
				title: 'Explorer le handicap'
			}
		},
		{
			title_first_part: 'Les troubles',
			title_second_part: 'psychiques',
			description: `L’Organisation Mondiale de la Santé estime que 20 à 25 % de la population sera touchée par un trouble psychique au cours de sa vie. Les troubles psychiques (addictions, Troubles Obsessionnels Compulsifs, bipolarité, schizophrénie, troubles du comportement alimentaire, anxiété, dépression…) se traduisent par des difficultés de relation à l’autre et font souvent l’objet d’un déni. L’écoute et l’accueil sont essentiels.`,
			list: [],
			image: '/slider/troubles-psychiques.png',
			picto: pictoPsychique,
			link: {
				href: '/handicaps',
				title: 'Explorer le handicap'
			}
		},
		{
			title_first_part: 'Les troubles',
			title_second_part: 'du spectre autistique',
			description: `Les personnes atteintes de troubles du spectre autistique peuvent également avoir des comportements inhabituels et d’énormes difficultés à établir des relations sociales considérées comme élémentaires ou comprendre ce qui n’est pas parfaitement explicite (sous-entendus, plaisanteries…). Selon la Haute Autorité de Santé, elles sont plus de 100 000 jeunes de moins de 20 ans et 600 000 adultes en France. `,
			list: [],
			image: '/slider/troubles-autistiques.png',
			picto: '',
			link: {
				href: '/handicaps',
				title: 'Explorer le handicap'
			}
		}
	];

	let swiperInstance;
	let swiperEl;
	let btnNext: HTMLElement;
	let btnPrev: HTMLElement;
	let paginationEl: HTMLElement;

	onMount(async () => {
		swiperInstance = await initSwiper(swiperEl, {
			slidesPerView: 1,
			spaceBetween: 40,
			navigation: {
				nextEl: btnNext,
				prevEl: btnPrev
			},
			pagination: {
				el: paginationEl,
				clickable: true,
				type: 'bullets' // explicite
			}
		});
	});

	onDestroy(() => {
		swiperInstance?.destroy(true, true);
	});
</script>

{#snippet SlideItem(slide)}
	<div class="swiper-slide">
		<div
			class="relative flex items-center gap-12 border border-theme-darkBlue pl-2 py-2 pr-10 rounded-xl text-theme-white"
		>
			<div class="flex-2">
				<img
					src={slide.image}
					alt="{slide.title_first_part} {slide.title_second_part}"
					class="min-w-130 max-w-130 h-160 w-full object-cover rounded-lg"
				/>
			</div>
			<div class="flex-1 flex flex-col gap-10 py-8">
				<h3 class="text-4.5xl leading-none">
					{slide.title_first_part} <br />
					<span class="text-theme-blue">{slide.title_second_part}</span>
				</h3>
				<div class="flex flex-col gap-6">
					<span class="uppercase leading-[80%]">Description</span>
					<p class="leading-[130%]">
						{slide.description}
					</p>
					<a
						href={slide.link.href}
						class="bg-[url('/src/lib/assets/button-explorer.svg')] w-52 h-13 bg-no-repeat bg-center bg-contain z-1"
					>
						<span class="sr-only">{slide.link.title}</span>
					</a>
				</div>
			</div>
			<img src="" alt="Picto" class="absolute bottom-10 left-10 w-55 object-contain" />
		</div>
	</div>
{/snippet}

<section class="flex flex-col gap-16 py-24">
	<h2 class="text-7xl leading-none text-theme-white px-16">
		<span class="text-theme-blue">Connaître les publics, </span> <br />
		c'est déjà les accueillir
	</h2>

	<div class="flex flex-col gap-8">
		<div bind:this={swiperEl} class="swiper px-16 overflow-hidden">
			<div class="swiper-wrapper px-16">
				{#each slides as slide, i (i)}
					{@render SlideItem(slide)}
				{/each}
			</div>
		</div>
		<div class="flex items-center gap-8 px-16">
			<div class="flex gap-1 p-1 rounded-2xl bg-theme-darkGrey w-fit">
				<button
					bind:this={btnPrev}
					class="btn-prev h-14 w-14 rounded-2xl flex items-center justify-center bg-theme-grey cursor-pointer"
				>
					<img src={arrowRight} alt="Précédent" class="rotate-180" />
				</button>
				<button
					bind:this={btnNext}
					class="btn-next h-14 w-14 rounded-2xl flex items-center justify-center bg-theme-black cursor-pointer"
				>
					<img src={arrowRight} alt="Suivant" />
				</button>
			</div>
			<div bind:this={paginationEl} class="swiper-pagination-custom flex gap-2"></div>
		</div>
	</div>
</section>

<style>
	:global(.swiper-pagination-custom .swiper-pagination-bullet) {
		width: 30px;
		height: 10px;
		border-radius: 12px;
		background: var(--color-theme-grey);
		opacity: 1;
		transition:
			width 0.3s ease,
			background 0.3s ease;
	}

	:global(.swiper-pagination-custom .swiper-pagination-bullet-active) {
		width: 50px;
		background: var(--color-theme-blue);
	}
</style> -->
