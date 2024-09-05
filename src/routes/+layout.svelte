<div class="outer-container">
	<div class="background">
		<div class="background-cover"></div>
		<div class="inner-container">
			<slot/>
		</div>
	</div>
</div>

<style>
	.outer-container {
		position: absolute;
		left: 0;
		top: 0;
		height: 100vh;
		width: 100vw;
	}

	.background {
		height: 100%;
		width: 100%;
		background-image: url('/scottherman1.jpg');
		background-repeat: no-repeat;
		background-size: 100% 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.background-cover {
		content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(255, 255, 255, 0.5);
	}

	.inner-container {
		z-index: 5;
	}
</style>