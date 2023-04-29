<script context="module" lang="ts">
	let componentIndex = 0;
</script>

<script lang="ts">
	import { onMount } from 'svelte';

	export let inputGroupName: string;
	export let tabNames: string[];

	let selectedTab = tabNames.length > 0 ? tabNames[0] : '';

	const id = `tabs-${name}-${componentIndex}`;

	onMount(() => componentIndex++);
</script>
