<link href="./node_modules/tachyons/css/tachyons.min.css" type="text/css">
<script>
	import Authentication from './Authentication.svelte';
	import AuthenticationForm from './Authentication-form.svelte';
	import Transactions from "./Transactions.svelte";

	let isAuthenticated = true;
	let wrongCredentials = false;
	const transactions = getTransactions();

	async function getTransactions() {
		const res = await fetch(`http://www.mocky.io/v2/5e3681443200007a00ae3c85`);
		const json = await res.json();

		if (res.ok) {
			return json;
		} else {
			throw new Error('An error occurred');
		}
	}

	const handleAuthentication = ({detail: {username, password}}) => {
		if (username === 'sergey' && password === 'webtalkto') {
			isAuthenticated = true;
			wrongCredentials = false;
		} else {
			wrongCredentials = true;
		}
	};
	const handleLogout = () => {
		isAuthenticated = false;
	};
	$: isNotAuthenticated = !isAuthenticated;
</script>

<div class="bg-light-gray flex justify-end ph2 pv3">
	<Authentication isAuthenticated={isAuthenticated} on:authentication={handleLogout}/>
</div>
{#if isNotAuthenticated}
	<AuthenticationForm on:credentials={handleAuthentication} wrongCredentials={wrongCredentials}/>
{/if}
{#if isAuthenticated}
	<div class="ph4">
		{#await transactions}
			<p>...waiting</p>
		{:then transactions}
			<Transactions transactions={transactions}/>
		{:catch error}
			<p style="color: red">{error.message}</p>
		{/await}
	</div>
{/if}

