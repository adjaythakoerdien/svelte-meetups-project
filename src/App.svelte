<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";
    // import TextInput from "./UI/TextInput.svelte";
    import Button from './UI/Button.svelte';
    import EditMeetup from "./MeetUps/EditMeetup.svelte";


    let meetups = [
        {
            id: 'm1',
            title: 'Coding bootcamp',
            subtitle: 'Learn to code in 2 hours',
            description: 'In this meetup we will talk about coding',
            imageUrl: 'https://images.unsplash.com/photo-1461749280684-dccba630e2f6?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1738&q=80',
            address: '27th Nerd Road, New York',
            contactEmail: 'code@test.com',
            isFavorite: false
        },
        {
            id: 'm2',
            title: 'Swim bootcamp',
            subtitle: 'Learn to swim in 2 hours',
            description: 'In this meetup we will swim',
            imageUrl: 'https://images.unsplash.com/photo-1600965962361-9035dbfd1c50?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1740&q=80',
            address: '27th Nerd Road, New York',
            contactEmail: 'code@test.com',
            isFavorite: false
        }
    ];

    let editMode;

    function addMeetup(event) {
        const newMeetup = {
            id: Math.random().toString(),
            title: event.detail.title,
            subtitle: event.detail.subtitle,
            description: event.detail.description,
            imageUrl: event.detail.imageUrl,
            contactEmail: event.detail.email,
            address: event.detail.address
        };

        // meetups.push(newMeetup); // DOES NOT WORK!
        meetups = [newMeetup, ...meetups];

        editMode = null;
    }

    function toggleFavorite(event) {
        const id = event.detail;
        const updatedMeetup = { ...meetups.find(m => m.id === id) };
        updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
        const meetupIndex = meetups.findIndex(m => m.id === id);
        const updatedMeetups = [...meetups];
        updatedMeetups[meetupIndex] = updatedMeetup;
        meetups = updatedMeetups;
    }
</script>

<style>
    main {
        margin-top: 5rem;
    }

    .meetup-controls {
        margin: 1rem;
    }
</style>

<Header />

<main>
    <div class="meetup-controls" role="presentation">
        <Button class="meetup-control" caption="New Meetup" on:click={() => editMode = 'add'} />
    </div>
    {#if editMode === 'add'}
        <EditMeetup on:save={addMeetup} />
    {/if}
    <MeetupGrid {meetups} on:togglefavorite="{toggleFavorite}" />
</main>
