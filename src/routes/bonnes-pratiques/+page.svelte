<script lang="ts">
	let { data } = $props();
	console.log('data : ', data);
</script>

<section class="px-16 py-24">
	<h2 class="uppercase text-[150px] leading-[80%] text-theme-blue text-center">Bonnes pratiques</h2>
	<div>
		<div>
			<input type="radio" name="filter" id="filter1" value="filter1" />
		</div>
		<div></div>
	</div>
</section>

{#each data.allPages as page (page.id)}
	<div>
		<p>{page.properties.Title.title[0].plain_text}</p>
	</div>
{/each}
