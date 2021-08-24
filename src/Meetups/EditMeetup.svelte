<script>
  import { createEventDispatcher } from 'svelte'
  import TextInput from '../UI/TextInput.svelte' 
  import Button from '../UI/Button.svelte'
  import Modal from '../UI/Modal.svelte'

  let title = '';
  let subtitle = '';
  let imageUrl = '';
  let address = '';
  let email = '';
  let description = '';

  const dispatch = createEventDispatcher()

  const submitForm = () => {
    dispatch('save', {
      title: title,
      subtitle: subtitle,
      imageUrl: imageUrl,
      address: address,
      email: email,
      description: description
    })
  }
</script>

<Modal title="Edit Meetup" on:cancel >
  <form on:submit|preventDefault={submitForm}>
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
      id="description" 
      label="Description" 
      value={description}
      on:input={ e => description = e.target.value }
    />
    <Button type="submit">Save</Button>
  </form>
</Modal>

<style>

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }

</style>