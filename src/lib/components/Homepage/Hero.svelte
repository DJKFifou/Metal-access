<script>
	import coeur from '$lib/assets/coeur.svg';
	// import buttonAudit from '$lib/assets/button-audit.svg';
</script>

<section
	class="relative h-lvh w-full flex flex-col items-center justify-center text-center gap-12 bg-cover bg-center px-18.75 pt-22.5"
>
	<img
		src="/bg-hero.svg"
		alt="Hero"
		class="absolute inset-0 w-full h-full object-center object-cover opacity-50 overflow-visible"
	/>
	<h1 class="font-fledora text-theme-white text-9xl! uppercase leading-[90%] z-1">
		L'accessibilité au <br />
		<span class="inline-flex">
			c
			<img src={coeur} alt="Coeur" class="w-30 h-30" />
			eur
		</span>
		du <span class="text-theme-blue">festival</span>
	</h1>
	<p class="text-lg font-semibold leading-[130%] text-white w-1/2 z-1">
		Metal AXS accompagne les festivals dans la mise en accessibilité de leurs évènements, du premier
		coup de basse au dernier rappel.
	</p>
	<a
		href="/mon-festival"
		class="bg-[url('/src/lib/assets/button-accessibilite-home.svg')] w-115 h-20 bg-no-repeat bg-center bg-contain z-1"
	>
		<span class="sr-only">Découvrir mon niveau d'accessibilité</span>
	</a>
</section>
