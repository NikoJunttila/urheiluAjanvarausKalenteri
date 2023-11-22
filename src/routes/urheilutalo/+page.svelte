<script lang="ts">
	import { ListBox, ListBoxItem } from '@skeletonlabs/skeleton';
	import type { day } from '$lib/types';
	import { getModalStore } from '@skeletonlabs/skeleton';
	import type { ModalSettings, ModalComponent, ModalStore } from '@skeletonlabs/skeleton';
	const modalStore = getModalStore();
    
    const modal: ModalSettings = {
	type: 'component',
    component: "modalComponentOne",
    title:"urheilutalo",
    body:"Ajanvaraus"
};
	const paikat: string[] = ['Peilisali', 'Juoksurata', 'Kiipeilyseinä', 'Yläsali', 'Tennis alue'];

	let peiliSaliMonday: day[] = [
		{ creator: 'Petteri', time: '10:00-12:00' },
		{ creator: 'Kalle', time: '12:30-14:00' }
	];
	let peiliSaliKeskiviikko: day[] = [
		{ creator: 'FR', time: '8:00-10:00' },
		{ creator: 'Kiia', time: '13:30-15:00' }
	];
	let peiliSaliLauantai: day[] = [
		{ creator: 'Ossi', time: '8:00-10:00' },
		{ creator: 'Pekka', time: '10:00-12:00' }
	];
	let juosurataTiistai: day[] = [{ creator: 'Kiia', time: '8:00' }];
	let valueSingle: string = 'Peilisali';
</script>

<header class="text-center">
	<h1 class="my-2">Urheilutalo</h1>
	<p>Ajanvaraukset</p>
</header>

<div class="container flex m-5">
	<div class="w-[30vw] max-w-[200px]">
		<ListBox>
			{#each paikat as p}
				<ListBoxItem
					class="border border-red-300 border-solid"
					bind:group={valueSingle}
					name="medium"
					value={p}>{p}</ListBoxItem
				>
			{/each}
		</ListBox>
	</div>
	<div class=" ml-5 w-full">
		<div class="grid grid-cols-7 grid-rows-1 h-[70vh]">
			<div>
				<span class="badge variant-filled-secondary">Maanantai</span>
				{#if valueSingle === 'Peilisali'}
					{#each peiliSaliMonday as d}
						<div class="border border-red-300 border-solid my-1 hover:bg-red-800">
							<p>varaaja</p>
							<p>
								{d.creator}
							</p>
							<p>Aika:{d.time}</p>
						</div>
					{/each}
				{/if}
			</div>
			<div>
				<span class="badge variant-filled-secondary"> Tiistai </span>
				{#if valueSingle === 'Juoksurata'}
					{#each juosurataTiistai as d}
						<div class="border border-red-300 border-solid my-1 hover:bg-red-800">
							<p>varaaja</p>
							<p>
								{d.creator}
							</p>
							<p>Aika:{d.time}</p>
						</div>
					{/each}
				{/if}
			</div>
			<div>
				<span class="badge variant-filled-secondary"> Keskiviikko </span>
				{#if valueSingle === 'Peilisali'}
					{#each peiliSaliKeskiviikko as d}
						<div class="border border-red-300 border-solid my-1 hover:bg-red-800">
							<p>varaaja</p>
							<p>
								{d.creator}
							</p>
							<p>Aika:{d.time}</p>
						</div>
					{/each}
				{/if}
			</div>
			<div>
				<span class="badge variant-filled-secondary"> Torstai </span>
			</div>
			<div>
				<span class="badge variant-filled-secondary"> Perjantai </span>
			</div>
			<div>
				<span class="badge variant-filled-secondary"> Lauantai </span>
				{#if valueSingle === 'Peilisali'}
					{#each peiliSaliLauantai as d}
						<div class="border border-red-300 border-solid my-1 hover:bg-red-800">
							<p>varaaja</p>
							<p>
								{d.creator}
							</p>
							<p>Aika:{d.time}</p>
						</div>
					{/each}
				{/if}
			</div>
			<div>
				<span class="badge variant-filled-secondary"> Sunnuntai </span>
			</div>
		</div>
		<div>
			<button on:click={() => modalStore.trigger(modal)} class="btn bg-secondary-600 mt-1 w-full">Varaa aika</button>
		</div>
	</div>
</div>

<style>
	.grid > div {
		text-align: center;
		border: solid black 1px;
		height: 100%;
	}
	span {
		padding: 5px !important;
		font-size: 1rem;
		margin-top: 5px;
		width: 100%;
	}
</style>
