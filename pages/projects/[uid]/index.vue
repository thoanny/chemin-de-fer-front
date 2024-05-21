<script setup>
const route = useRoute();
const router = useRouter();

const page = ref(null);
const TOTAL_PAGE = 12;
const ASPECT_RATIO = "210/297";
const selectedPageId = ref();
const menuPage = ref();

const items = ref([
  {
    label: "Modifier le projet",
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
    label: "Sommaire du projet",
    icon: "pi pi-list",
    command: () => {
      goToPage();
    },
  },
  {
    label: "Exporter le projet",
    icon: "pi pi-file-export",
    command: () => {},
  },
]);

const itemsMenu = ref([
  {
    label: "Modifier le nom",
    icon: "pi pi-pencil",
  },
  {
    label: "Changer le statut",
    icon: "pi pi-circle",
    items: [
      {
        label: "Indéfini",
        icon: "pi pi-circle-fill",
        color: "gray",
        command: () => {
          console.log("change status page:", selectedPageId.value);
        },
      },
      {
        label: "À faire",
        icon: "pi pi-circle-fill",
        color: "yellow",
      },
      {
        label: "En cours",
        icon: "pi pi-circle-fill",
        color: "orange",
      },
      {
        label: "À valider",
        icon: "pi pi-circle-fill",
        color: "blue",
      },
      {
        label: "Validé",
        icon: "pi pi-circle-fill",
        color: "green",
      },
    ],
  },
  {
    label: "Verouiller/déverouiller",
    icon: "pi pi-lock",
  },
  {
    separator: true,
  },
  {
    label: "Supprimer la page",
    icon: "pi pi-trash",
    color: "red",
  },
]);

const goToPage = (idx = null) => {
  if (!idx) {
    router.push({ path: route.path });
    page.value = null;
  } else {
    router.push({ path: route.path, query: { page: idx } });
    page.value = idx;
  }
};

const onRightClick = (event, idx) => {
  selectedPageId.value = idx;
  menuPage.value.show(event);
};

const onUpload = () => {};

onMounted(() => {
  page.value = route.query.page ?? null;
});
</script>

<template>
  <div class="flex">
    <h1 class="text-primary">Projet {{ route.params.uid }}</h1>
  </div>

  <div class="grid mb-4">
    <div class="col-fixed" style="width: 20rem">
      <div
        id="pages"
        class="grid grid-nogutter select-none"
        style="row-gap: 1rem"
      >
        <div class="col-6"></div>
        <div class="col-6" v-for="idx in TOTAL_PAGE">
          <div
            @click="goToPage(idx)"
            @contextmenu="onRightClick($event, idx)"
            :style="`aspect-ratio: ${ASPECT_RATIO}`"
            class="border-2 border-primary bg-white relative overflow-hidden cursor-pointer"
            :class="{
              'border-round-right border-left-1': idx % 2 === 1,
              'border-round-left border-right-1': idx % 2 === 0,
              'border-right-2 border-round-right': idx === TOTAL_PAGE, // Last
              'border-left-2 border-round-left': idx === 1, // First
            }"
          >
            <span
              class="absolute flex h-full w-full align-items-center justify-content-center p-2 text-center bg-black-alpha-50 text-white text-shadow text-sm"
            >
              <span>
                <span class="pi pi-lock mb-2"></span>
                <br />Page {{ idx }}
              </span>
            </span>
            <span
              class="absolute border-round-sm -bottom-2px bg-primary px-1 py-1 text-xs"
              :class="{
                '-right-2px': idx % 2 === 1,
                '-left-2px': idx % 2 === 0,
              }"
              >{{ idx }}</span
            >
            <img
              alt="user header"
              :src="`https://picsum.photos/id/1${idx}/130/185`"
              class="block h-full w-full"
              style="aspect-ratio: 210 / 297; object-fit: cover"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="sticky" style="top: 1rem">
        <div class="grid" v-if="page">
          <div class="col-8">
            <div class="flex gap-2 align-items-center mb-4">
              <span
                class="pi pi-lock text-2xl text-primary"
                v-tooltip="'Page verouillée'"
              ></span>
              <h2 class="my-0 text-3xl">Page {{ page }}</h2>
            </div>
            <PagePosts />
            <PageComments />
          </div>
          <div class="col-4">
            <div
              class="inline-flex gap-2 align-items-center text-blue-500 mb-3 py-2 px-3 border-round shadow-1 bg-white"
            >
              <span class="pi pi-circle-fill"></span>
              <span>À valider</span>
            </div>

            <div
              class="shadow-1 border-round bg-white mb-3 overflow-hidden border-1 border-white"
              :style="`aspect-ratio: ${ASPECT_RATIO}`"
            >
              <img
                :alt="`Aperçu de la page ${page}`"
                :src="`https://picsum.photos/id/1${page}/360/510`"
                class="block h-full w-full"
                style="aspect-ratio: 210 / 297; object-fit: cover"
              />
            </div>

            <div class="field">
              <FileUpload
                mode="basic"
                name="demo[]"
                url="/api/upload"
                accept="image/*"
                :maxFileSize="1000000"
                @upload="onUpload"
                :auto="true"
                chooseLabel="Choisir une image"
              />
            </div>
          </div>
        </div>
        <div v-else>
          <h2 class="mt-0">Sommaire</h2>

          <Card class="my-4 overflow-hidden" :pt="{ body: { class: 'p-0' } }">
            <template #content>
              <div
                class="p-datatable p-component p-datatable-responsive-scroll"
              >
                <div class="p-datatable-wrapper">
                  <table class="p-datatable-table">
                    <thead class="p-datatable-thead">
                      <tr>
                        <th>
                          <div class="p-column-header-content">
                            <span class="p-column-title">Articles</span>
                          </div>
                        </th>
                        <th>
                          <div
                            class="p-column-header-content justify-content-center"
                          >
                            <span class="p-column-title">Utilisateur 1</span>
                          </div>
                        </th>
                        <th>
                          <div
                            class="p-column-header-content justify-content-center"
                          >
                            <span class="p-column-title">Utilisateur 2</span>
                          </div>
                        </th>
                      </tr>
                    </thead>
                    <tbody class="p-datatable-tbody">
                      <tr>
                        <td colspan="3" class="font-bold text-gray-500">
                          Page 1
                        </td>
                      </tr>
                      <tr>
                        <td>
                          <a
                            href="https://google.com"
                            target="_blank"
                            class="text-primary font-semibold"
                            >Nom de l'article</a
                          >
                        </td>
                        <td class="text-center">
                          <span
                            class="pi pi-check-circle text-green-500"
                          ></span>
                        </td>
                        <td class="text-center">
                          <span class="pi pi-times-circle text-red-500"></span>
                        </td>
                      </tr>
                      <tr>
                        <td colspan="3" class="font-bold text-gray-500">
                          Page 2
                        </td>
                      </tr>
                      <tr>
                        <td colspan="3" class="font-bold text-gray-500">
                          Page 3
                        </td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </template>
          </Card>
        </div>
      </div>
    </div>
  </div>

  <ContextMenu ref="menuPage" :model="itemsMenu">
    <template #item="{ item, props }">
      <a
        v-ripple
        class="flex align-items-center"
        v-bind="props.action"
        :class="`text-${item.color}-500`"
      >
        <span :class="item.icon" />
        <span class="ml-2">{{ item.label }}</span>
        <Badge v-if="item.badge" class="ml-auto" :value="item.badge" />
        <i v-if="item.items" class="pi pi-angle-right ml-auto"></i>
      </a>
    </template>
  </ContextMenu>

  <div>
    <SpeedDial
      :model="items"
      direction="up"
      :tooltipOptions="{ position: 'right' }"
      showIcon="pi pi-ellipsis-v"
      hideIcon="pi pi-times"
      style="bottom: 1rem; right: 1rem"
      class="fixed"
    />
  </div>
</template>

<style></style>
