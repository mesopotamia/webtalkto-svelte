<script>
    import {createEventDispatcher} from "svelte";

    let username = '';
    let password = '';
    const dispatch =  createEventDispatcher();
    const performLogin = (e) => {
        dispatch('credentials', {
            username,
            password
        });
        console.log(username, password);
    };
    export let wrongCredentials;
</script>

<form on:submit|preventDefault={performLogin} class=" pa4 mt3">
    <h2>Sign On</h2>
    <label class="pb2">Username</label>
    <input bind:value={username}/>
    <label class="pb2">Password</label>
    <input bind:value={password}/>
    <div class="mt2">
        <button>Log in</button>
    </div>
    {#if wrongCredentials}
        <div class="red mt2">
            You've entered the wrong credentials
        </div>
    {/if}
</form>