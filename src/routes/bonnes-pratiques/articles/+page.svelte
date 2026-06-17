<script lang="ts">
	let { data } = $props();
	console.log('data:', data);
</script>

<h2>Articles et bonnes pratiques</h2>

{#each data.allPages as page (page.id)}
	<div>
		<p>{page.properties.Title.title[0].plain_text}</p>
	</div>
{/each}
