<script>
	import '../lib/styles.css';
	import ActionSheet from '$lib/action-sheet/ActionSheet.svelte';
	import ActionSheetButton from '$lib/action-sheet/ActionSheetButton.svelte';
	import Button from '$lib/button/Button.svelte';
	import Collection from '$lib/collection/Collection.svelte';
	import List from '$lib/list/List.svelte';
	import ListButtonRow from '$lib/list/ListButtonRow.svelte';
	import ListRow from '$lib/list/ListRow.svelte';
	import ListRowImage from '$lib/list/ListRowImage.svelte';
	import ListRowButtonTrailing from '$lib/list/ListRowButtonTrailing.svelte';
	import ListRowDefaultTrailing from '$lib/list/ListRowDefaultTrailing.svelte';
	import ListRowDisclosureTrailing from '$lib/list/ListRowDisclosureTrailing.svelte';
	import ListRowStepperTrailing from '$lib/list/ListRowStepperTrailing.svelte';
	import ListRowToggleTrailing from '$lib/list/ListRowToggleTrailing.svelte';
	import NavigationBar from '$lib/navigation-bar/NavigationBar.svelte';
	import NavigationBarLeading from '$lib/navigation-bar/NavigationBarLeading.svelte';
	import NavigationBarTrailing from '$lib/navigation-bar/NavigationBarTrailing.svelte';
	import NavigationBarSearchField from '$lib/navigation-bar/NavigationBarSearchField.svelte';
	import SegmentedControl from '$lib/segmented-control/SegmentedControl.svelte';
	import SegmentedControlButton from '$lib/segmented-control/SegmentedControlButton.svelte';
	import Sidebar from '$lib/sidebar/Sidebar.svelte';
	import SidebarNavigationBar from '$lib/sidebar/SidebarNavigationBar.svelte';
	import SidebarNavigationBarLeading from '$lib/sidebar/SidebarNavigationBarLeading.svelte';
	import SidebarNavigationBarTrailing from '$lib/sidebar/SidebarNavigationBarTrailing.svelte';
	import SidebarSection from '$lib/sidebar/SidebarSection.svelte';
	import SidebarSectionItem from '$lib/sidebar/SidebarSectionItem.svelte';
	import SidebarSectionAddItemButton from '$lib/sidebar/SidebarSectionAddItemButton.svelte';
	import TabBar from '$lib/tab-bar/TabBar.svelte';
	import TabBarButton from '$lib/tab-bar/TabBarButton.svelte';
	import Toolbar from '$lib/toolbar/Toolbar.svelte';
	import ToolbarButton from '$lib/toolbar/ToolbarButton.svelte';
	import ListTextFieldRow from '$lib/list/ListTextFieldRow.svelte';
</script>

<h1>Welcome to your library project</h1>
<p>Create your package using @sveltejs/package and preview/showcase your work with SvelteKit</p>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<!-- <Sidebar>
	<SidebarNavigationBar>
		<SidebarNavigationBarLeading slot="leading" />
		<SidebarNavigationBarTrailing slot="trailing" />
	</SidebarNavigationBar>
	<SidebarSection showHeading>
		<SidebarSectionItem />
		<SidebarSectionItem />
		<SidebarSectionItem />
		<SidebarSectionAddItemButton />
	</SidebarSection>
</Sidebar> -->
<div style="display: flex; flex-direction: column; gap: 24px; padding: 24px 16px">
	<Button state="disabled" />
	<Button />
	<Button type="bezeled-gray" />
	<Button type="bezeled" />
	<Button type="filled" />
	<Collection>
		<List showHeader showFooter>
			<ListButtonRow />
			<ListRow>
				<ListRowImage slot="image" />
				<ListRowButtonTrailing slot="trailing" />
			</ListRow>
			<ListRow>
				<ListRowImage slot="image" />
				<ListRowDefaultTrailing showDetail showSymbol showInfo showCheckmark showDisclosure />
			</ListRow>
			<ListRow>
				<ListRowDisclosureTrailing slot="trailing" />
			</ListRow>
			<ListRow>
				<ListRowStepperTrailing slot="trailing" />
			</ListRow>
			<ListRow>
				<ListRowToggleTrailing slot="trailing" />
			</ListRow>
			<ListTextFieldRow />
		</List>
	</Collection>
	<NavigationBar>
		<NavigationBarLeading slot="leading" />
		<NavigationBarTrailing slot="trailing-1" />
		<NavigationBarTrailing slot="trailing-2" />
		<NavigationBarTrailing slot="trailing-3" />
		<NavigationBarSearchField slot="search-field" />
	</NavigationBar>
	<SegmentedControl>
		<SegmentedControlButton />
		<SegmentedControlButton />
		<SegmentedControlButton />
	</SegmentedControl>
	<TabBar style="position: unset">
		<TabBarButton slot="button-1" />
		<TabBarButton slot="button-2" />
		<TabBarButton slot="button-3" />
		<TabBarButton slot="button-4" />
		<TabBarButton slot="button-5" />
	</TabBar>
	<Toolbar style="position: unset">
		<ToolbarButton />
		<ToolbarButton />
		<ToolbarButton />
		<ToolbarButton />
		<ToolbarButton />
	</Toolbar>
</div>
