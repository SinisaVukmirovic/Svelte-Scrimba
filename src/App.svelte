<script>
	import Emoji from './Emoji.svelte';
	import Container from './Container.svelte';
	import Header from './Header.svelte';
    import Buttons from './Buttons.svelte';
    import story from './story';

	let showHeader = false;
	
    let happyScore = 0;
    let storyIndex = 0;
    $: question = story[storyIndex];
    $: smileySays = question.end ? finalMessage() : question.smileySays;
    $: buttons = question.buttons;

    $: if (happyScore > 0 && storyIndex === 3) showHeader = true;

    function clickHandler(e) {
        if (e.detail.value === 'reset') {
			storyIndex = 0;
			happyScore = 0;
			showHeader = false;
		} else {
			storyIndex += 1;
			happyScore += e.detail.value;
		}
    }

    function finalMessage() {
		if (happyScore > 0) {
			return question.end.nice;
		} else if (happyScore < 0) {
			return question.end.mean;
		} else {
			return question.end.neutral;
		}
	}
</script>

{#if showHeader}
    <Header />
{/if}

<Container>
    <h1>{smileySays}</h1>
    <Emoji {happyScore} size={storyIndex+1} />
    <Buttons {buttons} on:click={clickHandler} />
</Container>

<style>
    h1 {
		text-align: center;
		background: #ff3e00;
		font-size: 2em;
      	padding: 0.3em .6em;
	  	color: white;
		border-radius: 50px;
	}
    :global(*) {
		box-sizing: border-box;
	}
	:global(body, html) {
		margin: 0;
		height: 100vh;
		overflow: hidden;
	}
</style>