<script lang="ts">
    import type { PageData } from './$types';
    interface Props {
        data: PageData;
    }

    let { data }: Props = $props();
</script>

<svelte:head>
	<title>Appeal Submitted | TrueOG</title>
</svelte:head>

<div class="content has-text-centered">
    <h2>Appeal Submitted</h2>
    <p>Your appeal has been submitted successfully. Your reference code is <b>{data.ref}</b>, you will need this to check the status of your report or if you need any further assistance.</p>
</div>