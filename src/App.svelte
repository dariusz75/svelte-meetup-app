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


const addMeetup = () => {
  const newMeetup = {
    id: Math.random().toString(),
    title,
    subtitle,
    description,
    imageUrl,
    address,
    email,
    descritption
  }

  meetups = [newMeetup, ...meetups]

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
  <Button caption="New Meetup" on:click={() => {editMode = 'add'}} />
    {#if editMode === 'add'}
      <EditMeetup />
    {/if}
  <MeetupGrid {meetups} on:togglefavourite={toggleFavourite} />
</main>

<style>
 
  main {
    margin-top: 5rem;
  }

</style>