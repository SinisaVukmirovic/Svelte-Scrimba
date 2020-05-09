<script>
	import Emoji from './Emoji.svelte';
	import Container from './Container.svelte';
	import Header from './Header.svelte';
	import Buttons from './Buttons.svelte';

	let showHeader = false;

    const buttons = [
        {value: 0,  text: 'ummmmmm......'},
        {value: 1,  text: 'I sure do!'},
        {value: -2, text: 'gross!'}
	]
	
    let score = 0;
</script>


{#if showHeader}
    <Header />
{/if}

<Container>
    Do you like pizza? Score: {score}
    <Buttons {buttons} on:click={(e) => {score += e.detail.value}} />
</Container>