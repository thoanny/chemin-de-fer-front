<script setup>
const route = useRoute();

const items = ref([
  {
    label: "Modifier le nom",
    icon: "pi pi-pen-to-square",
    command: () => {},
  },
  {
    label: "Ajouter une page",
    icon: "pi pi-plus",
    command: () => {},
  },
  {
    label: "Organiser les pages",
    icon: "pi pi-sort-alt",
    command: () => {
      navigateTo({
        name: "projects-uid-sorting",
        params: { uid: route.params.uid },
      });
    },
  },
  {
    label: "Sommaire",
    icon: "pi pi-list",
    command: () => {
      navigateTo({
        name: "projects-uid-summary",
        params: { uid: route.params.uid },
      });
    },
  },
]);
</script>

<template>
  <h1>Projet index</h1>

  <div>
    <SpeedDial
      :model="items"
      direction="up"
      :tooltipOptions="{ position: 'right' }"
      showIcon="pi pi-wrench"
      hideIcon="pi pi-times"
      style="bottom: 1rem; right: 1rem"
    />
  </div>
</template>
