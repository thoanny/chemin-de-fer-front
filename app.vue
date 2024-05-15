<script setup></script>
<template>
  <div>
    <header>
      <Toolbar style="border-radius: 0; padding: 0.5rem 1rem">
        <template #start>
          <nav>
            <ul class="flex align-items-center gap-4">
              <li>
                <NuxtLink :to="{ name: 'index' }">
                  <span class="pi pi-home"></span>
                  Accueil
                </NuxtLink>
              </li>
              <li>
                <NuxtLink :to="{ name: 'teams' }">
                  <span class="pi pi-user"></span>
                  Équipes
                </NuxtLink>
              </li>
              <li>
                <NuxtLink :to="{ name: 'projects' }">
                  <span class="pi pi-book"></span>
                  Projets
                </NuxtLink>
              </li>
              <!-- <li>
                <NuxtLink
                  :to="{ name: 'projects-uid', params: { uid: 'azertyuiop' } }"
                >
                  Projet A
                </NuxtLink>
              </li> -->
              <!-- <li>
                <NuxtLink
                  :to="{
                    name: 'projects-uid-summary',
                    params: { uid: 'azertyuiop' },
                  }"
                >
                  Sommaire du projet A
                </NuxtLink>
              </li> -->
              <!-- <li>
                <NuxtLink :to="{ name: 'legal-notice' }"
                  >Mentions légales</NuxtLink
                >
              </li> -->
            </ul>
          </nav>
        </template>

        <template #end>
          <div class="flex align-items-center gap-2">
            <Button label="Connexion" @click="navigateTo({ name: 'login' })" />
            <Button
              label="Inscription"
              @click="navigateTo({ name: 'signup' })"
              outlined
            />
            <Avatar label="A" />
          </div>
        </template>
      </Toolbar>
    </header>
    <div class="container">
      <NuxtPage />
    </div>
  </div>
</template>

<style scoped>
.container {
  /* max-width: 30rem; */
  /* margin: 0 auto; */
}
</style>
