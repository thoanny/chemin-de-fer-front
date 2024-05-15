<script setup>
const value = ref();
const form = ref({
  email: "",
  firstname: "",
  lastname: "",
});
</script>

<template>
  <h1>Inscription</h1>

  <div class="flex flex-column gap-2 mb-4">
    <Button label="S'inscrire avec Google" />
    <Button label="S'inscrire avec Facebook" />
  </div>

  <Divider class="my-4"> ou </Divider>

  <div class="flex flex-column gap-4">
    <div class="flex flex-column gap-2">
      <label for="email">Adresse e-mail</label>
      <InputText id="email" v-model="form.email" type="email" />
    </div>

    <div class="flex flex-column gap-2">
      <label for="firstname">Prénom</label>
      <InputText id="firstname" v-model="form.firstname" />
    </div>

    <div class="flex flex-column gap-2">
      <label for="lastname">Nom</label>
      <InputText id="lastname" v-model="form.lastname" />
    </div>

    <div class="flex flex-column gap-2">
      <label for="password">Mot de passe</label>
      <InputText id="password" v-model="form.password" type="password" />
    </div>

    <div class="flex flex-column gap-2">
      <label for="password-repeat">Répéter le mot de passe</label>
      <InputText
        id="password-repeat"
        v-model="form.passwordRepeat"
        type="password"
      />
    </div>

    <div class="flex align-items-center gap-2">
      <Checkbox v-model="form.terms" inputId="terms" :binary="true" />
      <label for="terms">
        Je suis d'accord avec les conditions d'utilisation
      </label>
    </div>

    <Button label="S'inscrire" />
  </div>
</template>
