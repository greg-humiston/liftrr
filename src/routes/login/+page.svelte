<script lang="ts">
	import { goto } from '$app/navigation';

	const handleSubmit = (event: SubmitEvent) => {
		event.preventDefault();

		if (event?.target) {
			const formData = new FormData(event.target as HTMLFormElement);
			const name = formData.get('username');

			// TODO: implement auth and session functionalities
			const instanceId = name + Math.round(Math.random() * 100).toString();
			goto(`/${instanceId}/home`);
		}
	};
</script>


<div class="tile-small">
	<div class="login-container">
		<form on:submit={handleSubmit}>
			<div class="form-header">
				<div>
					<span>Login to Liftrr</span>
				</div>
			</div>
			<div class="form-body">	
				<div class="input-container">
					<span class="form-label">Username:</span>	
					<input placeholder="Enter a username..." type="text" id="username" name="username">
				</div>
				<div class="input-container">
					<span class="form-label">Password:</span>	
					<input placeholder="Enter a password..." type="password" id="password" name="password">
				</div>
			</div>
			<div class="form-footer">
				<button type="submit">Submit</button>
			</div>
		</form>
	</div>
</div>

<style>
	.tile-small {
		background: rgba(255, 255, 255, 0.90);
		height: 200px;
		width: 350px;
		border-radius: 5px;
		box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
	}

	.login-container {
		padding: 25px;
		display: flex;
		flex-direction: column;
	}

	.input-container {
		margin: 20px 0px;
	}

	.form-label {
		font-family: Arial, Helvetica, sans-serif;
		font-weight: bold;
		color: black;
	}

	.form-header {
		display: flex;
		justify-content: center;
		font-family: Arial, Helvetica, sans-serif;
		font-weight: bold;
		font-size: 25px;
	}

	.form-footer {
		display: flex;
		justify-content: center;
	}
</style>