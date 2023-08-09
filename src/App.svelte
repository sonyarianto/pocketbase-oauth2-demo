<script>
  import PocketBase from 'pocketbase';

  async function signIn() {
    const pb = new PocketBase('https://api.buka.sh/v2');

    const authData = await pb.collection('oauth_users').authWithOAuth2({ provider: 'google' });

    // after the above you can also access the auth data from the authStore
    
    console.log(pb.authStore.isValid);
    console.log(pb.authStore.token);
    console.log(pb.authStore.model.id);

    console.log(authData);
  }
</script>

<button on:click={signIn}>Sign-in with Google</button>

