<script>
	import Emoji from './Emoji.svelte';
	import Container from './Container.svelte';
	import Header from './Header.svelte';
    import Buttons from './Buttons.svelte';
    import story from './story';

	let showHeader = false;
	
    let happyScore = 0;
    let storyIndex = 0;
    $: smileySays = story[storyIndex].smileySays;
    $: buttons = story[storyIndex].buttons;

    function clickHandler(e) {
        storyIndex +=1;
        happyScore += e.detail.value;
    }
</script>

{#if showHeader}
    <Header />
{/if}

<Container>
    <h1>{smileySays}</h1>
    <Emoji index={2} />
    <Buttons {buttons} on:click={clickHandler} />
</Container>