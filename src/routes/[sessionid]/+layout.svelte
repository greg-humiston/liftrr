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
				<div class="route-icon-container">
					<div>
						<button class="route-button">
							<img class="route-button-icon" src="/home.png" alt="home button">
						</button>
					</div>
					<div>
						<button class="route-button">
							<img class="route-button-icon" src="/exercise.png" alt="home button">
						</button>
					</div>
					<div>
						<button class="route-button">
							<img class="route-button-icon" src="/diet.png" alt="home button">
						</button>
					</div>
					<div>
						<button class="route-button">
							<img class="route-button-icon" src="/sleep.png" alt="home button">
						</button>
					</div>
					<div>
						<button class="route-button">
							<img class="route-button-icon" src="/settings.png" alt="home button">
						</button>
					</div>
				</div>
				<button class={`expand-button${expandedClassName}`} on:click={handleExpandClick}>
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

	.route-icon-container {
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: center;
		overflow: hidden;
	}

	.expand-button {
		background-color: hsl(0, 0%, 91%);
    border: 0px;
    cursor: pointer;
		padding-right: 5px;
		padding-left: 5px;
		border-left: 1px solid black;
	}

	.expand-button.expanded {
		border-right: 0px;
		border-top: 0px;
		border-bottom: 0px;
		border-left: 1px solid black;
	}

	.expand-button-icon {
		width: 15px;
		height: 15px;
	}

	.route-button {
		background-color: transparent;
    border: none;
    cursor: pointer;
		padding-right: 0px;
		margin-top: 10px;
		margin-bottom: 5px;
	}
	.route-button-icon {
		width: 50px;
		height: 50px;
	}

	.side-menu-inner-container {
		width: 25px;
		height: 80%;
		background-color: white;
		border: 1px solid black;
		border-left: 0px;
		border-radius: 0px 3px 3px 0px;
		transition: width .15s ease-in;
		display: flex;
		justify-content: flex-end;
	}

	.side-menu-inner-container.expanded {
		width: 100px;
		transition: width .10s ease-in;
	}
</style>