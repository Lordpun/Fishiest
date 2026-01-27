<template>
	<section class="message" v-if="!showPopup">
    <h4>You've been fished! 🐟</h4>
  </section>

	<section class="popup" v-if="showPopup">
		<section>
			<h3>Sign Up</h3>

			<form @submit.prevent="takeEmail">
				<label>
					Enter your email:<br>
					<input type="text" name="signUp" placeholder="Email">
				</label>

				<label>
					Password:<br>
					<input type="password" name="signUp" placeholder="Password">
				</label>

				<label>
					Confirm Password:<br>
					<input type="password" name="signUp" placeholder="Confirm Password">
				</label>

				<button>Sign Up</button>
			</form>
		</section>
	</section>
</template>

	<script setup>
		import { ref } from 'vue';

		let showPopup = ref(true);

		function takeEmail() {
			const email = document.getElementsByName("signUp")[0].value;

			if (email === "") {
				alert("Please enter a valid email.");
				return
			}

			showPopup.value = false;
		}
</script>

<style scoped>
	.message {
		text-align: center;
		font-size: 5rem;	
	}

	.popup {
		z-index: 1;
		width: 100%;
		height: 100%;
		background-color: rgba(0,0,0,0.4);
		position: absolute;
	  top: 50%;
	  left: 50%;
	  transform: translate(-50%, -50%);
	}

	.popup section {
		z-index: 2;
		background-color: #fff;
		text-align: center;
		border: 1px solid #ccc;
		border-radius: 2rem;
		width: 50%;
		height: 70%;
		position: absolute;
	  top: 50%;
	  left: 50%;
	  transform: translate(-50%, -50%);
	}

	label {
		display: block;
		margin: 2rem;
	}

	label input {
		border-radius: 3px;
		padding: 0.25rem;
		width: 50%;
	}

	button {
		background-color: #2596be;	
		color: #fff;
		padding: 0.5rem 2rem;
		border: none;
		border-radius: 10px;
	}

	button:hover {
		background-color: #187fa3;	
	}

	button:active {
		background-color: #53bfe6;
	}
</style>