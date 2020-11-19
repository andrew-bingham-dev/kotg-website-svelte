<script>
	import axios from 'axios';
	import * as Global from '../global.js';
	import Inview from 'svelte-inview';

	let formName = '';
	let formEmail = '';
	let formMessage = '';
	let contactData = {};
	let ref;

	async function onSubmit(e) {
		contactData = {
			name: formName,
			email: formEmail,
			message: formMessage,
		};
		const res = await axios.post(Global.baseURL + '/contacts', contactData, {
			headers: {
				'content-type': 'application/json',
			},
		});

		// Clear the form after send
		formName = '';
		formEmail = '';
		formMessage = '';
		contactData = {};
	}
</script>

<section bind:this={ref} class="white-section">
	<div id="contact">
		<div class="container">
			<Inview let:inView wrapper={ref}>
				{#if inView}
					<h2 class="heading expandText">Join my mailing list</h2>
				{:else}
					<h2 class="heading">Join my mailing list</h2>
				{/if}
			</Inview>
			<form class="content" on:submit|preventDefault={onSubmit}>
				<div>
					<label for="name">Name</label>
					<br />
					<input type="text" id="name" bind:value={formName} />
					<br />
					<label for="email">Email</label>
					<br />
					<input type="text" id="email" bind:value={formEmail} />
					<br />
					<label for="message">Type a message here (optional)</label>
					<br />
					<textarea rows="6" id="message" bind:value={formMessage} />
				</div>
				<div class="send-section"><button type="submit">Send</button></div>
			</form>
		</div>
	</div>
</section>
