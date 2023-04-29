<script context="module" lang="ts">
	let componentIndex = 0;
</script>

<script lang="ts">
	import { onMount } from 'svelte';

	export let inputGroupName: string;
	export let tabNames: string[];

	let selectedTab = tabNames.length > 0 ? tabNames[0] : '';

	const id = `tabs-${inputGroupName}-${componentIndex}`;

	onMount(() => componentIndex++);
</script>

<!--@component
Organize several views into tabbed sections.

### Props
- `inputGroupName': A name for the group of radio buttons that implement the tab
functionality. Used for accessibility.
- `tabNames`: A list of tab names.

### Slots
- `label`: If you want to include a header for the component. For the most 
accessible implementation, use a <legend> element.
- `content`: Display the different views here, using an if-block to handle the
different states.

### Slot Props
- `inputId`: The ID of the input element responsible for each tab. Use to create
a `<label>` element for each tab. The actual inputs are hidden.
- `tabName`: The name of the tab.
-->
<fieldset>
	<slot name="label" />
	{#each tabNames as tabName, index}
		{@const inputId = id + String(index)}
		<input type="radio" name={inputGroupName} bind:group={selectedTab} value={tabName} />
		<slot {inputId} {tabName} />
	{/each}
</fieldset>
<slot name="content" {selectedTab} />
