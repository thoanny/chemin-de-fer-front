<script setup>
const items = [
  {
    icon: "pi-book",
    title: "Projets",
    content:
      "Chaque projet est composé de pages, d'articles et de commentaires.",
  },
  {
    icon: "pi-users",
    title: "Équipes",
    content:
      "Créez des équipes pour limiter l'accès aux projets. Invitez les utilisateurs par e-mail.",
  },
  {
    icon: "pi-file",
    title: "Pages",
    content:
      "Ajoutez, supprimez et réorganisez les pages de vos projets facilement.",
  },
  {
    icon: "pi-file-export",
    title: "Exporter",
    content:
      "Exportez les éléments de votre projet en une seule page HTML facile à archiver.",
  },
  {
    icon: "pi-list-check",
    title: "Activités",
    content:
      "Les actions sont enregistrées pour suivre les modifications de vos projets.",
  },
  {
    icon: "pi-image",
    title: "Miniatures",
    content:
      "Attachez des miniatures à vos pages pour partager un aperçu de leur mise en page.",
  },
  {
    icon: "pi-tag",
    title: "Statut",
    content:
      "Modifiez le statut de chaque page pour connaître visuellement l'état de vos projets.",
  },
  {
    icon: "pi-thumbs-up",
    title: "Gratuit",
    content:
      'Pour profiter des avantages d\'un compte payant, <a href="https://www.patreon.com/thoanny/membership" target="_blank" class="text-primary">abonnez-vous à mon Patreon</a>&nbsp;!',
  },
];

const products = ref([
  {
    id: "0",
    feature: "Prix",
    free: "0 €",
    paid: "À partir de 5 €/mois",
    category: "Tarifs",
  },
  {
    id: "0",
    feature: "Nombre d'équipes",
    free: 1,
    paid: 10,
    category: "Équipes",
  },
  {
    id: "0",
    feature: "Nombre de membres",
    free: 5,
    paid: 50,
    category: "Équipes",
  },
  {
    id: "0",
    feature: "Nombre de projets actifs",
    free: 1,
    paid: 10,
    category: "Projets",
  },
  {
    id: "0",
    feature: "Nombre de pages par projets",
    free: 10,
    paid: 100,
    category: "Projets",
  },
  {
    id: "0",
    feature: "Limite totale du stockage",
    free: "50 Mo",
    paid: "250 Mo",
    category: "Stockage",
  },
]);
</script>

<template>
  <div>
    <div class="grid">
      <div class="col-3" v-for="item in items">
        <Card class="text-center h-full border-round-md">
          <template #header>
            <i
              class="pi mt-4 text-primary"
              :class="item.icon"
              style="font-size: 3rem"
            ></i>
          </template>
          <template #title
            ><span class="text-primary" v-html="item.title"></span
          ></template>
          <template #content>
            <p class="m-0" v-html="item.content"></p>
          </template>
        </Card>
      </div>
    </div>

    <Card class="my-4 overflow-hidden" :pt="{ body: { class: 'p-0' } }">
      <template #content>
        <DataTable
          :value="products"
          rowGroupMode="subheader"
          groupRowsBy="category"
        >
          <Column field="category" header="Catégorie"></Column>
          <Column field="feature" header="Fonctionnalité"></Column>
          <Column
            field="free"
            header="Compte gratuit"
            class="text-center"
            :pt="{ headerContent: { class: 'justify-content-center' } }"
          >
            <template #body="slotProps">
              <span
                class="pi pi-times-circle"
                style="color: var(--red-500); font-size: 1.25rem"
                v-if="slotProps.data.free === false"
              ></span>
              <span
                class="pi pi-check-circle"
                style="color: var(--green-500); font-size: 1.25rem"
                v-else-if="slotProps.data.free === true"
              ></span>
              <span v-else>{{ slotProps.data.free }}</span>
            </template>
          </Column>
          <Column
            field="paid"
            header="Compte payant"
            class="text-center"
            :pt="{ headerContent: { class: 'justify-content-center' } }"
          >
            <template #body="slotProps">
              <span
                class="pi pi-times-circle"
                style="color: var(--red-500); font-size: 1.25rem"
                v-if="slotProps.data.paid === false"
              ></span>
              <span
                class="pi pi-check-circle"
                style="color: var(--green-500); font-size: 1.25rem"
                v-else-if="slotProps.data.paid === true"
              ></span>
              <span v-else>{{ slotProps.data.paid }}</span>
            </template>
          </Column>
          <template #groupheader="slotProps">
            <span class="text-primary font-bold">{{
              slotProps.data.category
            }}</span>
          </template>
        </DataTable>
      </template>
    </Card>

    <div class="flex flex-column gap-2">
      <Message
        :closable="false"
        severity="success"
        style="background: white"
        icon="pi pi-send"
      >
        Message Content
      </Message>
    </div>
  </div>
</template>
