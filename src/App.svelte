<script>
import Header from './UI/Header.svelte'
import MeetupGrid from './Meetups/MeetupGrid.svelte'
import TextInput from './UI/TextInput.svelte'
import Button from './UI/Button.svelte'
import EditMeetup from './Meetups/EditMeetup.svelte'



let meetups = [
  {
    id: 'm1',
    title: 'HTML Basics',
    subtitle: 'Learn HTML in two hours',
    description: 'In this meetup we will have an expert who will teach you HTML fundamentals.',
    imageUrl: 'https://www.tutorialrepublic.com/lib/images/html-illustration.png',
    address: '123 Brixton Hill, London',
    email: 'codingmeatup@google.com',
    isFavourite: false
  },
  {
    id: 'm2',
    title: 'JS Basics',
    subtitle: 'Learn to code in two hours',
    description: 'In this meetup we will have an expert who will teach you Javascript fundamentals.',
    imageUrl: 'https://www.pozycjonusz.pl/wp-content/uploads/2019/05/java-script-SEO.jpg',
    address: '123 Brixton Hill, London',
    email: 'codingmeatup@google.com',
    isFavourite: false
  }
]

let editMode = null;


const addMeetup = (e) => {
  console.log('event is', e)
  const newMeetup = {
    id: Math.random().toString(),
    title: e.detail.title,
    subtitle: e.detail.subtitle,
    imageUrl: e.detail.imageUrl,
    address: e.detail.address,
    email: e.detail.email,
    description: e.detail.description
  }

  meetups = [newMeetup, ...meetups]
  editMode = null
}

const toggleFavourite = (e) => {
  const id = e.detail
  const updatedMeetup = {...meetups.find(meetup => meetup.id === id)}
  updatedMeetup.isFavourite = !updatedMeetup.isFavourite
  const meetupIndex = meetups.findIndex(meetup => meetup.id === id)
  const updatedMeetups = [...meetups]
  updatedMeetups[meetupIndex] = updatedMeetup
  meetups = updatedMeetups
}

</script>

<Header />
<main>
  <div class="meetup-controlls">
    <Button on:click={() => {editMode = 'add'}} >
      New Meetup
    </Button>
  </div>
    {#if editMode === 'add'}
      <EditMeetup on:save={addMeetup} />
    {/if}
  <MeetupGrid {meetups} on:togglefavourite={toggleFavourite} />
</main>

<style>
 
  main {
    margin-top: 5rem;
  }

  .meetup-controlls {
    margin: 1rem;
  }

</style>