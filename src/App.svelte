<script>
	import Emoji from './Emoji.svelte';
	import Container from './Container.svelte';
	import Header from './Header.svelte';
	import Buttons from './Buttons.svelte';

	let showHeader = false;
</script>

{#if showHeader}
	<Header />
{/if}

<Container>
	<!-- <Emoji index={0}></Emoji>
	<Emoji></Emoji>
	<Emoji index={2}></Emoji> -->

	<Buttons on:click={(e) => {(showHeader) = e.detail}} />
</Container>

<style>

</style>