<script>
	import oeilBlanc from '$lib/assets/oeil-blanc.svg';
	import arrowRight from '$lib/assets/arrow-right.svg';
</script>

<footer class="px-16 pt-20 flex flex-col gap-16 text-theme-white">
	<div class="flex justify-between">
		<a href="/" class="flex items-center gap-4 h-fit font-fledora">
			<img src={oeilBlanc} alt="Logo" class="inset-0 w-11.5 h-11.5 min-h-0 object-contain" />
			<span class="uppercase text-theme-white text-3.5xl leading-[92%]">Metal <br /> access</span>
		</a>
		<div class="flex gap-20">
			<div class="flex flex-col gap-6">
				<a
					href=""
					class="flex items-center gap-10 border-b border-theme-white/50 w-fit leading-[150%] py-3"
					>Accueil
					<img src={arrowRight} alt="Arrow" class="h-5 object-contain" />
				</a>
				<a
					href=""
					class="flex items-center gap-10 border-b border-theme-white/50 w-fit leading-[150%] py-3"
					>Bonnes pratiques
					<img src={arrowRight} alt="Arrow" class="h-5 object-contain" />
				</a>
				<a
					href=""
					class="flex items-center gap-10 border-b border-theme-white/50 w-fit leading-[150%] py-3"
					>Les handicaps
					<img src={arrowRight} alt="Arrow" class="h-5 object-contain" />
				</a>
				<a
					href=""
					class="flex items-center gap-10 border-b border-theme-white/50 w-fit leading-[150%] py-3"
					>Signalétique
					<img src={arrowRight} alt="Arrow" class="h-5 object-contain" />
				</a>
			</div>
			<div class="flex flex-col gap-6">
				<a
					href=""
					class="flex items-center gap-10 border-b border-theme-white/50 w-fit leading-[150%] py-3"
					>La fédération
					<img src={arrowRight} alt="Arrow" class="h-5 object-contain" />
				</a>
				<a
					href=""
					class="flex items-center gap-10 border-b border-theme-white/50 w-fit leading-[150%] py-3"
					>Faire mon audit
					<img src={arrowRight} alt="Arrow" class="h-5 object-contain" />
				</a>
				<a
					href=""
					class="flex items-center gap-10 border-b border-theme-white/50 w-fit leading-[150%] py-3"
					>Découvrir mon niveau d’accessibilité
					<img src={arrowRight} alt="Arrow" class="h-5 object-contain" />
				</a>
			</div>
		</div>
	</div>
</footer>
