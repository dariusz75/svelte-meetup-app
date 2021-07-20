<script>
import Header from './UI/Header.svelte'
import MeetupGrid from './Meetups/MeetupGrid.svelte'

const meetups = [
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
</script>

<Header />
<MeetupGrid meetups={meetups} />


<style>
  
</style>