<script>
  import { createEventDispatcher } from 'svelte'
  import TextInput from '../UI/TextInput.svelte' 
  import Button from '../UI/Button.svelte'

  let title = '';
  let subtitle = '';
  let imageUrl = '';
  let address = '';
  let email = '';
  let descritption = '';

  const dispatch = createEventDispatcher()

  const submitForm = () => {
    dispatch('save', {
      title: title,
      subtitle: subtitle,
      imageUrl: imageUrl,
      address: address,
      email: email,
      descritption: descritption
    })
  }
</script>

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
    id="descritption" 
    label="Descritption" 
    value={descritption}
    on:input={ e => descritption = e.target.value }
  />
  <Button type="submit" caption="Save" />
</form>

<style>

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }

</style>