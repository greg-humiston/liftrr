<script>
	// TODO: replace using runes
	let isExpanded = $state(false);

	const handleExpandClick = () => {
		isExpanded = !isExpanded;
		console.log('updated, isExpanded:', isExpanded);
	};

	let expandedClassName = $derived(isExpanded ? ' expanded' : '');
	let expandedButtonIconSrc = $derived(isExpanded ? "/arrow_back.png"  : "/arrow_forward.png" );
</script>

<div class="tile-full">
	<div class="side-menu-container">
		<div class={`side-menu-inner-container ${expandedClassName}`}>
			<button class="expand-button" on:click={handleExpandClick}>
				<img class="expand-button-icon" src={expandedButtonIconSrc} alt="sidebar expand arrow" />
			</button>

		</div>
	</div>
	<div><slot/></div>
</div>

<style>
	.tile-full {
		background: rgba(255, 255, 255, 0.9);
		height: 95vh;
		width: 95vw;
		border-radius: 5px;
		box-shadow: 10px 10px 10px rgba(0.75,0.75,0.75,0.75);
		border: 1px solid black;
		border-radius: 3px;
	}

	.side-menu-container {
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.expand-button {
		border: 1px;
		background-color: transparent;
    border: none;
    cursor: pointer;
		margin-top: 5px;
	}

	.expand-button-icon {
		width: 15px;
		height: 15px;
	}

	.side-menu-inner-container {
		width: 25px;
		height: 80%;
		background-color: white;
		border: 1px solid black;
		border-left-width: 0px;
		border-radius: 0px 3px 3px 0px;
		transition: width .15s ease-in;
		display: flex;
		justify-content: flex-end;
	}

	.side-menu-inner-container.expanded {
		width: 100px;
		transition: width .15s ease-in;
	}
</style>