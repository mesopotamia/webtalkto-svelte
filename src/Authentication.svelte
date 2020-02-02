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
    <h2 class="f5 ma0 pr3">You are logged in</h2>
    <button on:click={logout}>Log Out</button>
{:else}
    <h2 class="f5 ma0 pr3">You are logged out</h2>
{/if}