<script>
  import MeetupItem from './MeetupItem.svelte'

  export let meetups
</script>

<section class="meetups">
  {#each meetups as meetup }
    <MeetupItem
      id={meetup.id}    
      title={meetup.title} 
      subtitle={meetup.subtitle} 
      imageUrl={meetup.imageUrl} 
      description={meetup.description} 
      email={meetup.email} 
      address={meetup.address}
      isFavorite={meetup.isFavorite}
      on:showdetails
    />
      
  {/each}
</section>

<style>
  section {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 1rem;
  }

  @media(min-width: 768px) {
    section {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>