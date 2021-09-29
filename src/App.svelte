<script>
import meetups from './Meetups/meetupsStore.js'

import Header from './UI/Header.svelte'
import MeetupGrid from './Meetups/MeetupGrid.svelte'
import TextInput from './UI/TextInput.svelte'
import Button from './UI/Button.svelte'
import EditMeetup from './Meetups/EditMeetup.svelte'
import MeetupDetails from './Meetups/MeetupDetails.svelte'

let editMode = null;
let page = 'overview';
let pageData = {
  id: ''
}

const addMeetup = (e) => {
  editMode = null
}

const cancelEdit = () => {
  editMode = null
}

const showDetails = (e) => {
  page = 'details'
  pageData.id = e.detail
}

const closeDetails = () => {
  page = 'overview'
  pageData.id = ''
}

</script>

<Header />
<main>
  {#if page === 'overview'}
  <div class="meetup-controlls">
    <Button on:click={() => {editMode = 'add'}} >
      New Meetup
    </Button>
  </div>
    {#if editMode === 'add'}
      <EditMeetup on:save={addMeetup} on:cancel={cancelEdit}/>
    {/if}
  <MeetupGrid meetups={$meetups} on:showdetails={showDetails} />
{:else}
<MeetupDetails id={pageData.id} on:close={closeDetails} />
{/if}
</main>

<style>
 
  main {
    margin-top: 5rem;
  }

  .meetup-controlls {
    margin: 1rem;
  }

</style>