<script setup>
import { useDialog } from "primevue/usedialog";
const dialog = useDialog();

const UserLoginComponent = defineAsyncComponent(() =>
  import("@/components/UserLogin.vue")
);

const UserSignupComponent = defineAsyncComponent(() =>
  import("@/components/UserSignup.vue")
);

const showLoginForm = () => {
  dialog.open(UserLoginComponent, {
    props: {
      header: "Connexion",
      style: {
        width: "30rem",
      },
      modal: true,
    },
  });
};

const showSignupForm = () => {
  dialog.open(UserSignupComponent, {
    props: {
      header: "Créer un compte",
      style: {
        width: "30rem",
      },
      modal: true,
    },
  });
};

const menu = ref();
const items = ref([
  {
    separator: true,
  },
  {
    label: "Mon compte",
    icon: "pi pi-user",
    command: () => {
      return navigateTo({ name: "account" });
    },
  },
  {
    label: "Déconnexion",
    icon: "pi pi-power-off",
  },
]);

const toggle = (event) => {
  menu.value.toggle(event);
};
</script>
<template>
  <div class="mx-4">
    <header>
      <Toolbar
        style="padding: 0.25rem 1rem 0.25rem 1.5rem"
        class="container my-4"
      >
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
                <NuxtLink :to="{ name: 'legal-notice' }"
                  >Mentions légales</NuxtLink
                >
              </li> -->
            </ul>
          </nav>
        </template>

        <template #center>
          <span class="text-lg font-bold text-primary">Chemin de fer</span>
        </template>

        <template #end>
          <div class="flex align-items-center gap-2">
            <Button label="Connexion" @click="showLoginForm" size="small" />
            <Button
              label="Inscription"
              @click="showSignupForm"
              size="small"
              outlined
            />
            <Avatar
              image="https://gravatar.com/avatar/423de53e1cbf220c85b4ee13b4db1dad3289c1f2257a1783dfd439a758be45c1?d=mp"
              class="cursor-pointer border-round overflow-hidden"
              @click="toggle"
            />
            <Menu ref="menu" id="overlay_menu" :model="items" :popup="true">
              <template #submenuheader="{ item }">
                <span class="text-primary font-bold">{{ item.label }}</span>
              </template>
              <template #start>
                <button
                  v-ripple
                  class="relative overflow-hidden w-full p-link flex align-items-center p-1 text-color border-noround"
                >
                  <Avatar
                    image="https://gravatar.com/avatar/423de53e1cbf220c85b4ee13b4db1dad3289c1f2257a1783dfd439a758be45c1?d=mp"
                    class="mr-2 bg-primary border-round overflow-hidden"
                  />
                  <span class="inline-flex flex-column">
                    <span class="font-bold">Anthony</span>
                    <span class="text-sm">Compte gratuit</span>
                  </span>
                </button>
              </template>
            </Menu>
          </div>
        </template>
      </Toolbar>
    </header>
    <div class="container">
      <NuxtPage />
    </div>
    <footer></footer>
    <DynamicDialog />
  </div>
</template>
