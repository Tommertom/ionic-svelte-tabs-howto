# HOW-TO Ionic Svelte - Ionic Tabs
This repo shows how to implement Ionic Tabs in SvelteKit. 

## Why this HowTo
Implementing Ionic Tabs requires deep integration with the routing system. That is why this HowTo uses SvelteKit as guide. The challenge lies in the fact that we like to use the router paths to navigate to various tabs.

## No SvelteKit -> no worries
If you don't use SvelteKit but Svelte with Vite, then please use IonTabsLegacy.svelte and the implementation in https://github.com/Tommertom/svelte-ionic-app/tree/main/src/routes/components/tabs/%5Btab%5D

Or copy IonTab.svelte from `ionic-svelte` and adapt to your liking (when your router supports layout structures, like Routify, then this should be doable). Future support for non-Kit is something I am considering.

## Codesandbox
Want to dive into an example? Use the link below to the code-sandbox. After opening the link, please pop-up the render window to see the results.

NOTE - not working due to Vite4 not yet available for codesandbox
https://codesandbox.io/s/github/Tommertom/ionic-svelte-tabs-howto

So, you can also clone this repo:
`npx degit https://github.com/Tommertom/ionic-svelte-tabs-howto ionic-tabs`

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
	import IonTabs from './IonTabs.svelte';

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

## Migration from legacy
See https://github.com/Tommertom/svelte-ionic-npm/blob/main/CHANGELOG.md#05350536