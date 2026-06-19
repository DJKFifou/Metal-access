<script lang="ts">
	import { onMount } from 'svelte';
	import riveSrc from '$lib/assets/festival_accessible_scene.riv?url';

	type Answer = 'oui' | 'non' | 'jspp' | null;

	let { answers = [null, null, null, null] }: { answers: Answer[] } = $props();

	const STATE_MACHINES = [
		'state_entree_pmr',
		'state_signaliques',
		'state_stand_access',
		'state__espace_pmr'
	];
	const INPUT_NAMES = ['isOpen_entree', 'isOpen_signalitique', 'isOpen_stand', 'isOpen_espace'];

	let canvas: HTMLCanvasElement;
	let rive: import('@rive-app/canvas').Rive | null = null;
	let loaded = false;

	onMount(async () => {
		const { Rive } = await import('@rive-app/canvas');

		rive = new Rive({
			src: riveSrc,
			canvas,
			artboard: 'festival_accessible_scene',
			stateMachines: STATE_MACHINES,
			autoplay: false,
			onLoad: () => {
				rive!.resizeDrawingSurfaceToCanvas();
				// Force tous les inputs à false sur chaque state machine
				STATE_MACHINES.forEach((sm, i) => {
					const inputs = rive!.stateMachineInputs(sm);
					if (inputs) {
						const input = inputs.find((inp) => inp.name === INPUT_NAMES[i]);
						if (input) input.value = false;
					}
				});
				rive!.play(STATE_MACHINES);
				loaded = true;
			}
		});

		const observer = new ResizeObserver(() => {
			rive?.resizeDrawingSurfaceToCanvas();
		});
		observer.observe(canvas);

		return () => {
			observer.disconnect();
			rive?.cleanup();
		};
	});

	function syncInputs() {
		if (!rive || !loaded) return;
		STATE_MACHINES.forEach((sm, i) => {
			const inputs = rive!.stateMachineInputs(sm);
			if (!inputs) return;
			const input = inputs.find((inp) => inp.name === INPUT_NAMES[i]);
			if (input) input.value = answers[i] === 'oui';
		});
	}

	$effect(() => {
		answers.forEach(() => {});
		syncInputs();
	});
</script>

<canvas bind:this={canvas} class="w-full h-full"></canvas>
