<script lang="ts">
    import type { PageData } from './$types';
    import PunishTable from '$lib/PunishTable.svelte';

    interface Props {
        data: PageData;
    }

    let { data }: Props = $props();

    let viewableBans = $state(data.punishments.bans);
    if (viewableBans.length > 9) {
        viewableBans = viewableBans.slice(0, 9)
    }

    let viewableMutes = $state(data.punishments.mutes);
    if (viewableMutes.length > 9) {
        viewableMutes = viewableMutes.slice(0, 9)
    }

</script>

<svelte:head>
	<title>{data.staffName}'s Staff Profile | TrueOG</title>
</svelte:head>

<container class="container">
    <div class="content has-text-centered">
        <br>
        <h1>{data.staffName}'s Staff Profile</h1>
        <p>{data.staffName} has issued <b>{data.totalPunishments}</b> punishments: {data.punishments.bans.length} bans and {data.punishments.mutes.length} mutes.</p>
        <p><a href="/player/{data.staffUuid}">Click here to view their punishment history.</a></p>
    </div>
    <div class="columns">
        <div class="column staffog-gib-padding">
            <h1 class="title has-text-centered">Recent Bans</h1>
            <PunishTable entryList={viewableBans} punishType="bans"/>
        </div>
        <div class="column staffog-gib-padding">
            <h1 class="title has-text-centered">Recent Mutes</h1>
            <PunishTable entryList={viewableMutes} punishType="mutes"/>
        </div>
    </div>
</container>