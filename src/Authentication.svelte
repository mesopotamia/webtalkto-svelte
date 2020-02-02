<script>
    import {createEventDispatcher} from "svelte";

    export let isAuthenticated;
    const dispatch = createEventDispatcher();
    function login() {
        dispatch('authentication', true);
    }
    const logout = () => {
        dispatch('authentication', false);
    };
</script>

{#if isAuthenticated}
    <h1>You are logged in</h1>
    <button on:click={logout}>Log Out</button>
{:else}
    <h1>You are logged out</h1>
    <button on:click={login}>Log In</button>
{/if}