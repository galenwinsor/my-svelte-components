<script lang="ts">
	import { Meta, Template, Story } from '@storybook/addon-svelte-csf';
	import Tabs from './Tabs.svelte';
</script>

<Meta title="Tabs" component={Tabs} />

<Template>
	<Tabs inputGroupName="my-tabs" tabNames={['A', 'B', 'C']} let:inputId let:tabName>
		<legend slot="label">My Tabs</legend>
		<label for={inputId}>{tabName}</label>
		<div slot="content" let:selectedTab>
			{selectedTab}
		</div>
	</Tabs>
</Template>

<Story name="Example" args={{}} />
