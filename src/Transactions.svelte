<script>
    export let transactions;
</script>

<h2>Transactions</h2>
{#each transactions as {merchant, amount, date} }
    <div class="flex justify-between pv2">
        <span class="w-25">{merchant}</span>
        <span class="w-25">{amount}</span>
        <span class="w-25">{date}</span>
    </div>
{/each}
