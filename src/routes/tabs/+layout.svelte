<script lang="ts">
	import IonTabs from './IonTabsRouter.svelte';

	import { videocam, pin } from 'ionicons/icons';
	import { onMount } from 'svelte';

	const myTabs = [
		{
			label: 'Explain',
			icon: pin,
			tab: 'test1'
		},
		{ label: 'Controllers', icon: videocam, tab: 'test2' }
	];

	const logStuff = () => {};
</script>

<IonTabs slot="bottom" tabs={myTabs} ionTabsWillChange={logStuff} ionTabsDidChange={logStuff}
	><slot /></IonTabs
>
