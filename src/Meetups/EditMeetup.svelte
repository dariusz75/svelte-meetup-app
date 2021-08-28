<script>
  import { createEventDispatcher } from 'svelte'
  import TextInput from '../UI/TextInput.svelte' 
  import Button from '../UI/Button.svelte'
  import Modal from '../UI/Modal.svelte'

  import { isEmpty, isValidEmail } from '../helpers/validation';

  let title = '';
  let subtitle = '';
  let address = '';
  let imageUrl = '';
  let email = '';
  let description = '';

  $: validTitle = !isEmpty(title);
  $: validSubtitle = !isEmpty(subtitle);
  $: validAddress = !isEmpty(address);
  $: validImageUrl = !isEmpty(imageUrl);
  $: validEmail = isValidEmail(email);
  $: validDescription = !isEmpty(description);
  $: validForm = 
      validTitle && 
      validSubtitle && 
      validAddress && 
      validImageUrl && 
      validEmail && 
      validDescription;


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
      valid={validTitle}
      validityMessage="Please enter a title"
      value={title}
      on:input={ e => title = e.target.value }
    />
    <TextInput 
      id="subtitle" 
      type="text"
      label="Subtitle"
      valid={validSubtitle}
      validityMessage="Please enter a subtitle"
      value={subtitle}
      on:input={ e => subtitle = e.target.value }
    />
    <TextInput 
      id="address" 
      type="text"
      label="Address"
      valid={validAddress}
      validityMessage="Please enter an Address"
      value={address}
      on:input={ e => address = e.target.value }
    />
    <TextInput 
      id="imageUrl" 
      type="text"
      label="Image URL" 
      valid={validImageUrl}
      validityMessage="Please enter valid url"
      value={imageUrl}
      on:input={ e => imageUrl = e.target.value }
    />
    <TextInput 
      id="email" 
      type="email"
      label="Email"
      valid={validEmail}
      validityMessage="Please enter a valid email"
      value={email}
      on:input={ e => email = e.target.value }
    />
    <TextInput 
      controlType="textarea"
      rows="3"
      id="description" 
      label="Description" 
      valid={validDescription}
      validityMessage="Please enter valid description"
      value={description}
      on:input={ e => description = e.target.value }
    />
  </form>
  <div slot="footer">
    <Button mode="outline" on:click={()=>dispatch('cancel')}>Cancel</Button>
    <Button type="button" disabled={!validForm} on:click={submitForm}>Save</Button>
  </div>
</Modal>

<style>

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }

</style>