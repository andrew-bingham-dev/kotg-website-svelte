<script>
	import axios from 'axios';
	let formName = '';
	let formEmail = '';
	let formMessage = '';
	let contactData = {};

	async function onSubmit(e) {
		contactData = {
			name: formName,
			email: formEmail,
			message: formMessage,
		};
		const res = await axios.post('http://localhost:1337/contacts', contactData, {
			headers: {
				'content-type': 'application/json',
			},
		});

		// console.table(contactData);
	}
</script>

<section class="white-section">
	<div id="contact">
		<div class="container">
			<h2 class="heading">Contact</h2>
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
