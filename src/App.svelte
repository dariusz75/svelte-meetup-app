<script>
import meetups from './Meetups/meetupsStore.js'

import Header from './UI/Header.svelte'
import MeetupGrid from './Meetups/MeetupGrid.svelte'
import TextInput from './UI/TextInput.svelte'
import Button from './UI/Button.svelte'
import EditMeetup from './Meetups/EditMeetup.svelte'

let editMode = null;

const addMeetup = (e) => {
  const meetupData = {
    title: e.detail.title,
    subtitle: e.detail.subtitle,
    imageUrl: e.detail.imageUrl,
    address: e.detail.address,
    email: e.detail.email,
    description: e.detail.description
  }

  meetups.addMeetup(meetupData)
  editMode = null
}

const cancelEdit = () => {
  editMode = null
}

const toggleFavourite = (e) => {
  const id = e.detail
  meetups.toggleFavorite(id)
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
      <EditMeetup on:save={addMeetup} on:cancel={cancelEdit}/>
    {/if}
  <MeetupGrid meetups={$meetups} on:togglefavourite={toggleFavourite} />
</main>

<style>
 
  main {
    margin-top: 5rem;
  }

  .meetup-controlls {
    margin: 1rem;
  }

</style>