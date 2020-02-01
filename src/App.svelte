<script>
	let name = 'world';
	let loggedIn = false;
	function login() {
		loggedIn = true;
	}
	const logout = () => {
		loggedIn = false
	};
</script>

{#if loggedIn}
	<h1>You are logged in</h1>
	<button on:click={logout}>Log Out</button>
	{:else}
	<h1>You are logged out</h1>
	<button on:click={login}>Log In</button>
{/if}


