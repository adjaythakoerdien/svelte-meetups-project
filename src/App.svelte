<script>
    import Header from './UI/Header.svelte';
    import MeetupItem from "./MeetUps/MeetupItem.svelte";

    const meetups = [
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
</script>

<style>
    #meetups {
        margin-top: 5rem;
    }
</style>

<Header />

<section id="meetups">
    {#each meetups as meetup}
        <MeetupItem
        title = {meetup.title}
        subtitle = {meetup.subtitle}
        imageUrl = {meetup.imageUrl}
        description = {meetup.description}
        email = {meetup.email}
        address = {meetup.address}
        />
    {/each}
</section>
