<script setup>
const value = ref();
const form = ref({
  email: "",
  firstname: "",
  lastname: "",
});
</script>

<template>
  <div>
    <Button label="Se connecter avec Google" class="w-full" />

    <Divider class="my-4"> ou </Divider>

    <div class="">
      <div class="field">
        <label for="email">Adresse e-mail</label>
        <InputText
          id="email"
          v-model="form.email"
          type="email"
          class="w-full"
          autocomplete="off"
          aria-describedby="email-help"
        />
        <small id="email-help"
          >Utilisez la même adresse e-mail que votre compte Patreon pour
          profiter des avantages d'un compte payant.</small
        >
      </div>

      <div class="formgrid grid">
        <div class="field col">
          <label for="firstname">Prénom</label>
          <InputText
            id="firstname"
            v-model="form.firstname"
            class="w-full"
            autocomplete="off"
          />
        </div>

        <div class="field col">
          <label for="lastname">Nom</label>
          <InputText
            id="lastname"
            v-model="form.lastname"
            class="w-full"
            autocomplete="off"
          />
        </div>
      </div>

      <div class="formgrid grid">
        <div class="field col">
          <label for="password">Mot de passe</label>
          <Password
            inputId="password"
            v-model="form.password"
            class="w-full"
            toggleMask
          />
        </div>

        <div class="field col">
          <label for="password-repeat">Répéter</label>
          <Password
            inputId="password-repeat"
            v-model="form.passwordRepeat"
            class="w-full"
            toggleMask
          />
        </div>
      </div>

      <div class="field">
        <div class="flex align-items-center gap-2">
          <Checkbox v-model="form.terms" inputId="terms" :binary="true" />
          <label for="terms">
            Je suis d'accord avec les conditions d'utilisation
          </label>
        </div>
      </div>

      <Button label="S'inscrire" />
    </div>
  </div>
</template>
