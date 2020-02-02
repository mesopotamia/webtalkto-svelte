<link href="./node_modules/tachyons/css/tachyons.min.css" type="text/css">
<script>
	import Authentication from './Authentication.svelte';
	let isAuthenticated = true;
	const handleAuthentication = ({detail: isAuthenticatedEvent}) => {
		isAuthenticated = isAuthenticatedEvent;
	};
	$: loggedOut = !isAuthenticated;
</script>

<div class="bg-light-gray flex justify-end ph2 pv3">
	<Authentication isAuthenticated={isAuthenticated} on:authentication={handleAuthentication}/>
</div>

<div>Logged out: {loggedOut}</div>

