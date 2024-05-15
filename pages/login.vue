<script setup>
const form = ref({});

const handleForgotPassword = () => {
  return navigateTo({ name: "forgot-password" });
};
</script>

<template>
  <h1>Connexion</h1>

  <div class="flex flex-column gap-2 mb-4">
    <Button label="Se connecter avec Google" />
    <Button label="Se connecter avec Facebook" />
  </div>

  <Divider class="my-4"> ou </Divider>

  <div class="flex flex-column">
    <div class="flex flex-column mb-4">
      <label for="email" class="mb-2">Adresse e-mail</label>
      <InputText id="email" v-model="form.email" type="email" />
    </div>

    <div class="flex flex-column mb-4">
      <label for="password" class="mb-2">Mot de passe</label>
      <InputText id="password" v-model="form.password" type="password" />
    </div>

    <Button label="Se connecter" class="mb-2" />
    <Button label="Mot de passe oublié ?" @click="handleForgotPassword" link />
  </div>
</template>
