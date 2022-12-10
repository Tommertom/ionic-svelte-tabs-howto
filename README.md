# HOW-TO Ionic Svelte - Ionic Tabs

This repo shows how to implement Ionic Tabs in SvelteKit. 

## Why this HowTo
Implementing Ionic Tabs requires deep integration with the routing system. That is why this HowTo uses SvelteKit as guide. The challenge lies in the fact that we like to use the router paths to navigate to various tabs.

## Codesandbox
Want to dive into an example? Use the link below to the code-sandbox. After opening the link, please pop-up the render window to see the results.

NOTE - not working due to Vite upgrade
https://codesandbox.io/s/github/Tommertom/ionic-svelte-tabs-howto

## Steps to implement 
1. The IonTabs component needs to placed in a `+layout.svelte` 
2. Make sure it has a `<slot/>` in between, so the pages can be rendered in that router outlet
3. Define the subroutes in the folder where the IonTabs layout-file is placed
4. Each subroute needs to have its content wrapped in a `ion-tab` element, and this element should have prop `tab` properly filled

Some pointers:
- when there is no proper route provided, the tab-bar will throw a warning and navigate to `/`
- if no `tab` prop is provided, the tab-bar will not work 

## API info
API for the `+layout.svelte` file:
```
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
```

API for any `+page.svelte` file that has tab-content:

```
<ion-tab tab="test2">
HERE YOUR CONTENT
</ion-tab>
```
Make sure the ion-tab has prop `tab` pointing to the name of the route. So in this case, the route could be `whatever/whenever/tabs/test2`.

