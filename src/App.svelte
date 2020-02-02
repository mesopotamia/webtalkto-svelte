<link href="./node_modules/tachyons/css/tachyons.min.css" type="text/css">
<script>
	import Authentication from './Authentication.svelte';
	import AuthenticationForm from './Authentication-form.svelte';
	let isAuthenticated = false;
	let wrongCredentials = false;
	const handleAuthentication = ({detail: {username, password}}) => {
		if (username === 'sergey' && password === 'webtalkto') {
			isAuthenticated = true;
			wrongCredentials = false;
		} else {
			wrongCredentials = true;
		}
	};
	const handleLogout =() => {
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

