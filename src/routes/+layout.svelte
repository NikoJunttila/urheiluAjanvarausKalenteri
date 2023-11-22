<script lang="ts">
	import '../app.postcss';
	import { AppShell, AppBar, type PopupSettings, popup } from '@skeletonlabs/skeleton';
	import { Avatar } from '@skeletonlabs/skeleton';
	import { Modal } from '@skeletonlabs/skeleton';
    import type { ModalComponent } from '@skeletonlabs/skeleton';
	import { initializeStores } from '@skeletonlabs/skeleton';
	import ModalForm from '$lib/ModalForm.svelte';
initializeStores();
const modalRegistry: Record<string, ModalComponent> = {
	modalComponentOne: { ref: ModalForm },

};

	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
	const popupFeatured: PopupSettings = {
		// Represents the type of event that opens/closed the popup
		event: 'click',
		// Matches the data-popup value on your popup element
		target: 'popupFeatured',
		// Defines which side of your trigger the popup will appear
		placement: 'bottom'
	};
	let name = "Kiia"

</script>

<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<a href="/">
					<strong class="text-xl uppercase">Urheilu kalenteri</strong>
				</a>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<div class="card p-4 variant-filled-primary" data-popup="popupFeatured">
					<form class="flex flex-col items-center">
						<Avatar src="https://images.unsplash.com/photo-1555169062-013468b47731?q=80&w=1974&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" width="w-32" rounded="rounded-full" />
						<input class="input mt-3" bind:value={name} type="text" name="name" />
					</form>
					<div class="arrow variant-filled-primary" />
				</div>
				<button class="btn variant-filled" use:popup={popupFeatured}>Käyttäjä</button>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<Modal components={modalRegistry}/>

	<!-- Page Route Content -->
	<slot />
</AppShell>