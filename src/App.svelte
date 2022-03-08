<script>
    import Header from './UI/Header.svelte';
    import MeetupGrid from "./MeetUps/MeetupGrid.svelte";
    import TextInput from "./UI/TextInput.svelte";
    import Button from "./UI/Button.svelte";

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

    form {
        width: 30rem;
        max-width: 90%;
        margin: auto;
    }
</style>

<Header />
<main>
    <form on:submit|preventDefault={addMeetup}>
        <TextInput
            id="title"
            label="Title"
            value="{title}"
            type="text"
            on:input="{(event) => (title = event.target.value)}"
        />
        <TextInput
            id="subtitle"
            label="Subtitle"
            value="{subtitle}"
            type="text"
            on:input="{(event) => (subtitle = event.target.value)}"
        />
        <TextInput
            id="address"
            label="Address"
            value="{address}"
            type="text"
            on:input="{(event) => (address = event.target.value)}" />
        <TextInput
            id="imageUrl"
            label="Image URL"
            value="{imageUrl}"
            type="text"
            on:input="{(event) => (imageUrl = event.target.value)}" />
        <TextInput
            id="email"
            label="Email"
            value="{email}"
            type="email"
            on:input="{(event) => (email = event.target.value)}" />
        <TextInput
            id="description"
            label="Description"
            value="{description}"
            controlType="textarea"
            rows="3"
            on:input="{(event) => description = event.target.value}" />
        <Button type="submit" caption="Add Meetup" />
    </form>
    <MeetupGrid {meetups}/>
</main>
