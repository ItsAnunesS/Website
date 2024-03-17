<script setup lang="ts">
const supabase = useSupabaseClient()
const email = ref('')

const signInWithOtp = async () => {
  const { error } = await supabase.auth.signInWithOtp({
    email: email.value,
    options: {
      emailRedirectTo: 'http://localhost:3000/confirm',
    }
  })
  if (error) console.log(error)
}

async function signInWithDiscord() {
  const { data, error } = await supabase.auth.signInWithOAuth({
    provider: 'discord',
    options: {
      emailRedirectTo: 'http://localhost:3000/confirm',
    }
  })
  if (error) console.log(error)
}
</script>
<template>
  <div>
    <button @click="signInWithDiscord">
      discord
    </button>
    <button @click="signInWithOtp">
      Sign In with E-Mail
    </button>
    <input
        v-model="email"
        type="email"
    />
  </div>
</template>
