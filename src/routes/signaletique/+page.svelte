<script>
	import AsideRessource from '$lib/components/AsideRessource.svelte';

	const tags = ['Backstage & staff', 'Festivaliers', 'Artistes', 'Bénévoles', 'Production'];

	const ressources = [
		{
			id: 1,
			image: {
				url: '/ressources/toilettes.svg',
				alt: 'Toilettes accessibles'
			},
			title: 'Toilettes',
			tag: 'Backstage & staff',
			properties: {
				tag: 'Backstage & staff',
				description:
					'Des installations de douche accessibles permettent aux festivaliers en situation de handicap de profiter pleinement des événements multi-jours.',
				utilisation: [
					{
						name: 'Artistes',
						image: {
							url: '/ressources/artistes.png',
							alt: 'Artistes'
						}
					},
					{
						name: 'Artistes',
						image: {
							url: '/ressources/artistes.png',
							alt: 'Artistes'
						}
					}
				],
				informations: [
					{
						title: 'Configuration',
						description:
							"Douches à l'italienne sans rebord, espace de 1,50m × 1,50m, siège de douche rabattable fixé au mur, barre d'appui horizontale et verticale."
					},
					{
						title: 'Équipements',
						description:
							'Pommeau de douche à hauteur réglable, robinetterie à levier ou détection automatique, crochets à hauteur accessible (max 1,30m du sol).'
					},
					{
						title: 'Accès',
						description:
							"Porte d'au moins 90cm, poignée de tirage côté extérieur, espace de manœuvre libre devant la porte. Revêtement antidérapant obligatoire."
					},
					{
						title: 'Assistance',
						description:
							"Personnel disponible et formé. Système d'appel d'urgence dans chaque cabine. Horaires communiqués à l'avance."
					}
				]
			}
		},
		{
			id: 2,
			image: {
				url: '/ressources/douches.svg',
				alt: 'Douches accessibles'
			},
			title: 'Douches',
			tag: 'Backstage & staff',
			properties: {
				tag: 'Backstage & staff',
				description:
					'Des installations de douche accessibles permettent aux festivaliers en situation de handicap de profiter pleinement des événements multi-jours.',
				utilisation: [
					{
						name: 'Artistes',
						image: {
							url: '/ressources/artistes.png',
							alt: 'Artistes'
						}
					},
					{
						name: 'Artistes',
						image: {
							url: '/ressources/artistes.png',
							alt: 'Artistes'
						}
					}
				],
				informations: [
					{
						title: 'Configuration',
						description:
							"Douches à l'italienne sans rebord, espace de 1,50m × 1,50m, siège de douche rabattable fixé au mur, barre d'appui horizontale et verticale."
					},
					{
						title: 'Équipements',
						description:
							'Pommeau de douche à hauteur réglable, robinetterie à levier ou détection automatique, crochets à hauteur accessible (max 1,30m du sol).'
					},
					{
						title: 'Accès',
						description:
							"Porte d'au moins 90cm, poignée de tirage côté extérieur, espace de manœuvre libre devant la porte. Revêtement antidérapant obligatoire."
					},
					{
						title: 'Assistance',
						description:
							"Personnel disponible et formé. Système d'appel d'urgence dans chaque cabine. Horaires communiqués à l'avance."
					}
				]
			}
		},
		{
			id: 3,
			image: {
				url: '/ressources/restauration.svg',
				alt: 'Restauration accessible'
			},
			title: 'Restauration',
			tag: 'Festivaliers',
			properties: {
				tag: 'Festivaliers',
				description:
					'Des installations de douche accessibles permettent aux festivaliers en situation de handicap de profiter pleinement des événements multi-jours.',
				utilisation: [
					{
						name: 'Artistes',
						image: {
							url: '/ressources/artistes.png',
							alt: 'Artistes'
						}
					},
					{
						name: 'Artistes',
						image: {
							url: '/ressources/artistes.png',
							alt: 'Artistes'
						}
					}
				],
				informations: [
					{
						title: 'Configuration',
						description:
							"Douches à l'italienne sans rebord, espace de 1,50m × 1,50m, siège de douche rabattable fixé au mur, barre d'appui horizontale et verticale."
					},
					{
						title: 'Équipements',
						description:
							'Pommeau de douche à hauteur réglable, robinetterie à levier ou détection automatique, crochets à hauteur accessible (max 1,30m du sol).'
					},
					{
						title: 'Accès',
						description:
							"Porte d'au moins 90cm, poignée de tirage côté extérieur, espace de manœuvre libre devant la porte. Revêtement antidérapant obligatoire."
					},
					{
						title: 'Assistance',
						description:
							"Personnel disponible et formé. Système d'appel d'urgence dans chaque cabine. Horaires communiqués à l'avance."
					}
				]
			}
		}
	];

	let selectedFilter = $state('all');
	let selectedColor = $state('#eaf8ff');
	let ressourcesWithSvg = $state([]);
	let searchQuery = $state('');
	let filteredRessources = $derived(
		(ressourcesWithSvg.length ? ressourcesWithSvg : ressources)
			.filter((r) => selectedFilter === 'all' || r.tag === selectedFilter)
			.filter((r) => r.title.toLowerCase().includes(searchQuery.toLowerCase()))
	);

	async function loadSvgWithColor(url, color) {
		const res = await fetch(url);
		let svgText = await res.text();

		svgText = svgText.replace(/(<rect[^>]*?)fill="[^"]*"/, `$1fill="${color}"`);

		return `data:image/svg+xml;charset=utf-8,${encodeURIComponent(svgText)}`;
	}

	async function updateSvgs() {
		ressourcesWithSvg = await Promise.all(
			ressources.map(async (r) => ({
				...r,
				computedSvgUrl: await loadSvgWithColor(r.image.url, selectedColor)
			}))
		);
	}

	$effect(() => {
		updateSvgs();
	});
	let selectedRessource = $state(null);

	function closeAside() {
		selectedRessource = null;
	}
</script>

{#snippet Ressource(ressource)}
	<button
		onclick={() => (selectedRessource = ressource)}
		class="border border-theme-lightGrey rounded-xl px-2 pt-2 pb-4 flex flex-col items-center gap-4 shadow-card-ressource h-fit cursor-pointer"
	>
		<img
			src={ressource.computedSvgUrl ?? ressource.image.url}
			alt={ressource.image.alt}
			class="w-full h-37 object-contain rounded-lg"
		/>
		<span class="leading-[130%] text-2xl text-theme-white">
			{ressource.title}
		</span>
	</button>
{/snippet}

<div class="pt-24">
	<section class="flex flex-col gap-16 px-16 py-24">
		<h2 class="uppercase text-[150px] leading-[80%] text-theme-blue text-center">
			Bonnes pratiques
		</h2>
		<div class="flex flex-col gap-24">
			<div class="flex gap-4 justify-center">
				<div class="flex rounded-5xl border border-white/20 overflow-hidden p-1">
					<div>
						<input
							type="radio"
							name="filter"
							id="filter_all"
							value="all"
							class="peer sr-only"
							bind:group={selectedFilter}
							checked
						/>
						<label
							for="filter_all"
							class="px-4 py-2 bg-theme-black text-theme-white cursor-pointer peer-checked:bg-theme-blue peer-checked:text-theme-black rounded-5xl block"
							>Tous</label
						>
					</div>
					{#each tags as tag, i (i)}
						<div>
							<input
								type="radio"
								name="filter"
								id="filter_{tag}"
								value={tag}
								class="peer sr-only"
								bind:group={selectedFilter}
							/>
							<label
								for="filter_{tag}"
								class="px-4 py-2 bg-theme-black text-theme-white cursor-pointer peer-checked:bg-theme-blue peer-checked:text-theme-black rounded-5xl block"
								>{tag}</label
							>
						</div>
					{/each}
				</div>
				<input
					type="text"
					name="search"
					id="search"
					placeholder="Rechercher..."
					bind:value={searchQuery}
					class="text-white/70 px-4.5 bg-theme-black border border-white/20 rounded-4xl py-2"
				/>
			</div>
		</div>
		<div class="flex flex-col gap-4">
			<h3 class="text-4.5xl leading-none text-theme-white">Des signalétiques prêtes à imprimer</h3>
			<p class="text-theme-white/80 text-lg leading-[130%]">
				Rendre votre festival accessible passe aussi par une signalétique claire et adaptée.
				Retrouvez ici l'ensemble des panneaux dont vous avez besoin, organisés par zone et par type
				de public. Filtrez, choisissez vos formats et téléchargez ce qui correspond à votre
				événement.
			</p>
		</div>
		<div class="flex gap-22">
			<div class="flex-2 grid grid-cols-3 gap-8">
				{#if filteredRessources.length > 0}
					{#each filteredRessources as ressource (ressource.id)}
						{@render Ressource(ressource)}
					{/each}
				{:else}
					<p class="text-theme-white/80">Aucune ressource.</p>
				{/if}
			</div>
			<div class="flex-1 flex flex-col gap-8 text-theme-white">
				<div class="flex flex-col gap-6">
					<h3 class="text-4.5xl leading-none">Personnaliser</h3>
					<hr />
				</div>
				<p class="leading-[150%]">
					Personnalisez les couleurs de votre festival, téléchargez des panneaux qui s'intègrent à
					votre DA.
				</p>
				<div class="bg-theme-white p-4 rounded-lg flex flex-col gap-4">
					<span class="text-theme-black text-2xl font-fledora leading-none"
						>Sélecteur de couleur</span
					>
					<input type="color" bind:value={selectedColor} class="w-full h-25 rounded" />
					<span class="text-theme-black text-lg leading-none">
						Couleur sélectionnée : <span class="uppercase">{selectedColor}</span>
					</span>
				</div>
			</div>
		</div>
	</section>
</div>

{#if selectedRessource}
	<AsideRessource {closeAside} {selectedRessource} />
{/if}
