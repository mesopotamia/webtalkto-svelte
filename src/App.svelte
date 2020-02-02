<script>
	import Authentication from './Authentication.svelte';
	let isAuthenticated = true;
	const handleAuthentication = ({detail: isAuthenticatedEvent}) => {
		isAuthenticated = isAuthenticatedEvent;
	};
	$: loggedOut = !isAuthenticated;
</script>

<Authentication isAuthenticated={isAuthenticated} on:authentication={handleAuthentication}/>
<div>Logged out: {loggedOut}</div>

