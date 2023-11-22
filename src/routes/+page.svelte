<script lang="ts">
		import type { LocationEx } from "$lib/types";
	const sijainnit : LocationEx[] = [
		{name:"urheilutalo",description:"Kokkolan urheilutalolta löytyy useita eri urheilu mahdollisuuksia kuten tennis, sulkapallo, seinäkiipeily yms...",image:"https://www.finna.fi/Cover/Show?source=Solr&id=museovirasto.FA755BD73E8AA1F011ED48E3DC91F417&index=0&size=large"},
		{name:"uimahalli",description:"pääsee uimaan", image:"https://www.kokkola.fi/uploads/2021/01/2021/01/20190330-dsc_2354-scaled.jpg"},
		{name:"kirkonmäen urheilukenttä", description:"yleisurheilu kenttä missä myös tennis pelaus mahdollisuus", image:"https://lh5.googleusercontent.com/p/AF1QipPAdzC6A-v93L3goBem3D5Za0UzChRYO71swXbd=w408-h544-k-no"},
		{name:"kipparihalli", description:"lämmin tekonurmi halli, pesäpallo alue, tekonurmea pihalla, tennis alue", image:"https://lh5.googleusercontent.com/p/AF1QipNJ-w9wN50kiXV5O_N1ejynUfyaTBzbjQQHswcZ=w408-h544-k-no"}
	]
</script>	
<div class="container h-full m-5">
	<div class="parent">
		{#each sijainnit as loc}
		<a href="/{loc.name}" class="m-1">
			<div class="flex flex-col h-full w-full items-center card card-hover box p-3">
					<img class="card-header max-h-[300px]"  src={loc.image} alt={loc.name} /> 
				<h2 class="text-center py-1">{loc.name}</h2>
				<section class="p-2">{loc.description}</section>
			</div>
		</a>
		{/each}
	</div>
</div>
<style>
	.parent {
display: grid;
grid-template-columns: repeat(3, 1fr);
grid-template-rows: repeat(3, 1fr);
}
h2{
	font-size: 1.25rem;
}
</style>