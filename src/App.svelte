<script>
import Header from './UI/Header.svelte'
import MeetupGrid from './Meetups/MeetupGrid.svelte'
import TextInput from './UI/TextInput.svelte'

let id = '';
let title = '';
let subtitle = '';
let description = '';
let imageUrl = '';
let address = '';
let email = '';
let descritption = '';

let meetups = [
  {
    id: 'm1',
    title: 'HTML Basics',
    subtitle: 'Learn HTML in two hours',
    description: 'In this meetup we will have an expert who will teach you HTML fundamentals.',
    imageUrl: 'https://www.tutorialrepublic.com/lib/images/html-illustration.png',
    address: '123 Brixton Hill, London',
    email: 'codingmeatup@google.com'
  },
  {
    id: 'm2',
    title: 'JS Basics',
    subtitle: 'Learn to code in two hours',
    description: 'In this meetup we will have an expert who will teach you Javascript fundamentals.',
    imageUrl: 'https://www.pozycjonusz.pl/wp-content/uploads/2019/05/java-script-SEO.jpg',
    address: '123 Brixton Hill, London',
    email: 'codingmeatup@google.com'
  }
]

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

</script>

<Header />
<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput 
      id="title" 
      type="text"
      label="Title" 
      value={title}
      on:input={ e => title = e.target.value }
    />
    <TextInput 
      id="subtitle" 
      type="text"
      label="Subtitle" 
      value={subtitle}
      on:input={ e => subtitle = e.target.value }
    />
    <TextInput 
      id="address" 
      type="text"
      label="Address" 
      value={address}
      on:input={ e => address = e.target.value }
    />
    <TextInput 
      id="imageUrl" 
      type="text"
      label="Image URL" 
      value={imageUrl}
      on:input={ e => imageUrl = e.target.value }
    />
    <TextInput 
      id="email" 
      type="email"
      label="Email" 
      value={email}
      on:input={ e => email = e.target.value }
    />
    <TextInput 
      controlType="textarea"
      rows="3"
      id="descritption" 
      label="Descritption" 
      value={descritption}
      on:input={ e => descritption = e.target.value }
    />
    <button>Submit</button>
  </form>
  <MeetupGrid {meetups} />
</main>

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