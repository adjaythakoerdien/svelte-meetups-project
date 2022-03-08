<script>
    import Header from './UI/Header.svelte';
    import MeetupGrid from "./MeetUps/MeetupGrid.svelte";

    let title = '';
    let subtitle = '';
    let address = '';
    let email = '';
    let description = '';
    let imageUrl = '';

    let meetups = [
        {
            id: 'm1',
            title: 'Coding bootcamp',
            subtitle: 'Learn to code in 2 hours',
            description: 'In this meetup we will talk about coding',
            imageUrl: 'https://images.unsplash.com/photo-1461749280684-dccba630e2f6?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1738&q=80',
            address: '27th Nerd Road, New York',
            contactEmail: 'code@test.com'
        },
        {
            id: 'm2',
            title: 'Swim bootcamp',
            subtitle: 'Learn to swim in 2 hours',
            description: 'In this meetup we will swim',
            imageUrl: 'https://images.unsplash.com/photo-1600965962361-9035dbfd1c50?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1740&q=80',
            address: '27th Nerd Road, New York',
            contactEmail: 'code@test.com'
        }
    ]

    function addMeetup() {
        const newMeetup = {
            id: Math.random().toString(),
            title: title,
            subtitle: subtitle,
            description: description,
            imageUrl: imageUrl,
            contactEmail: email,
            address: address
        };

        meetups = [
            newMeetup,
            ...meetups
        ];
    }
</script>

<style>
    main {
        margin-top: 5rem;
    }
</style>

<Header />
<main>
    <form on:submit|preventDefault={addMeetup}>
        <div class="form-control">
            <label for="title">Titel</label>
            <input type="text" id="title" bind:value={title}>
        </div>
        <div class="form-control">
            <label for="subtitle">Subtitle</label>
            <input type="text" id="subtitle" bind:value={subtitle}>
        </div>
        <div class="form-control">
            <label for="address">Address</label>
            <input type="text" id="address" bind:value={address}>
        </div>
        <div class="form-control">
            <label for="imageUrl">Image URL</label>
            <input type="text" id="imageUrl" bind:value={imageUrl}>
        </div>
        <div class="form-control">
            <label for="email">Email</label>
            <input type="email" id="email" bind:value={email}>
        </div>
        <div class="form-control">
            <label for="description">Description</label>
            <textarea rows="3" id="description" bind:value={description}></textarea>
        </div>
        <button type="submit">Submit</button>

    </form>
    <MeetupGrid {meetups}/>
</main>
