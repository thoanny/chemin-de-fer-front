<script setup>
const getSeverity = (product) => {
  switch (product.inventoryStatus) {
    case "INSTOCK":
      return "success";

    case "LOWSTOCK":
      return "warning";

    case "OUTOFSTOCK":
      return "danger";

    default:
      return null;
  }
};

const products = ref([
  {
    id: "1000",
    code: "f230fh0g3",
    name: "Bamboo Watch",
    description: "Product Description",
    image: "bamboo-watch.jpg",
    price: 65,
    category: "Accessories",
    quantity: 24,
    inventoryStatus: "INSTOCK",
    rating: 5,
  },
  {
    id: "1001",
    code: "nvklal433",
    name: "Black Watch",
    description: "Product Description",
    image: "black-watch.jpg",
    price: 72,
    category: "Accessories",
    quantity: 61,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1002",
    code: "zz21cz3c1",
    name: "Blue Band",
    description: "Product Description",
    image: "blue-band.jpg",
    price: 79,
    category: "Fitness",
    quantity: 2,
    inventoryStatus: "LOWSTOCK",
    rating: 3,
  },
  {
    id: "1003",
    code: "244wgerg2",
    name: "Blue T-Shirt",
    description: "Product Description",
    image: "blue-t-shirt.jpg",
    price: 29,
    category: "Clothing",
    quantity: 25,
    inventoryStatus: "INSTOCK",
    rating: 5,
  },
  {
    id: "1004",
    code: "h456wer53",
    name: "Bracelet",
    description: "Product Description",
    image: "bracelet.jpg",
    price: 15,
    category: "Accessories",
    quantity: 73,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1005",
    code: "av2231fwg",
    name: "Brown Purse",
    description: "Product Description",
    image: "brown-purse.jpg",
    price: 120,
    category: "Accessories",
    quantity: 0,
    inventoryStatus: "OUTOFSTOCK",
    rating: 4,
  },
  {
    id: "1006",
    code: "bib36pfvm",
    name: "Chakra Bracelet",
    description: "Product Description",
    image: "chakra-bracelet.jpg",
    price: 32,
    category: "Accessories",
    quantity: 5,
    inventoryStatus: "LOWSTOCK",
    rating: 3,
  },
  {
    id: "1007",
    code: "mbvjkgip5",
    name: "Galaxy Earrings",
    description: "Product Description",
    image: "galaxy-earrings.jpg",
    price: 34,
    category: "Accessories",
    quantity: 23,
    inventoryStatus: "INSTOCK",
    rating: 5,
  },
  {
    id: "1008",
    code: "vbb124btr",
    name: "Game Controller",
    description: "Product Description",
    image: "game-controller.jpg",
    price: 99,
    category: "Electronics",
    quantity: 2,
    inventoryStatus: "LOWSTOCK",
    rating: 4,
  },
  {
    id: "1009",
    code: "cm230f032",
    name: "Gaming Set",
    description: "Product Description",
    image: "gaming-set.jpg",
    price: 299,
    category: "Electronics",
    quantity: 63,
    inventoryStatus: "INSTOCK",
    rating: 3,
  },
  {
    id: "1010",
    code: "plb34234v",
    name: "Gold Phone Case",
    description: "Product Description",
    image: "gold-phone-case.jpg",
    price: 24,
    category: "Accessories",
    quantity: 0,
    inventoryStatus: "OUTOFSTOCK",
    rating: 4,
  },
  {
    id: "1011",
    code: "4920nnc2d",
    name: "Green Earbuds",
    description: "Product Description",
    image: "green-earbuds.jpg",
    price: 89,
    category: "Electronics",
    quantity: 23,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1012",
    code: "250vm23cc",
    name: "Green T-Shirt",
    description: "Product Description",
    image: "green-t-shirt.jpg",
    price: 49,
    category: "Clothing",
    quantity: 74,
    inventoryStatus: "INSTOCK",
    rating: 5,
  },
  {
    id: "1013",
    code: "fldsmn31b",
    name: "Grey T-Shirt",
    description: "Product Description",
    image: "grey-t-shirt.jpg",
    price: 48,
    category: "Clothing",
    quantity: 0,
    inventoryStatus: "OUTOFSTOCK",
    rating: 3,
  },
  {
    id: "1014",
    code: "waas1x2as",
    name: "Headphones",
    description: "Product Description",
    image: "headphones.jpg",
    price: 175,
    category: "Electronics",
    quantity: 8,
    inventoryStatus: "LOWSTOCK",
    rating: 5,
  },
  {
    id: "1015",
    code: "vb34btbg5",
    name: "Light Green T-Shirt",
    description: "Product Description",
    image: "light-green-t-shirt.jpg",
    price: 49,
    category: "Clothing",
    quantity: 34,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1016",
    code: "k8l6j58jl",
    name: "Lime Band",
    description: "Product Description",
    image: "lime-band.jpg",
    price: 79,
    category: "Fitness",
    quantity: 12,
    inventoryStatus: "INSTOCK",
    rating: 3,
  },
  {
    id: "1017",
    code: "v435nn85n",
    name: "Mini Speakers",
    description: "Product Description",
    image: "mini-speakers.jpg",
    price: 85,
    category: "Clothing",
    quantity: 42,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1018",
    code: "09zx9c0zc",
    name: "Painted Phone Case",
    description: "Product Description",
    image: "painted-phone-case.jpg",
    price: 56,
    category: "Accessories",
    quantity: 41,
    inventoryStatus: "INSTOCK",
    rating: 5,
  },
  {
    id: "1019",
    code: "mnb5mb2m5",
    name: "Pink Band",
    description: "Product Description",
    image: "pink-band.jpg",
    price: 79,
    category: "Fitness",
    quantity: 63,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1020",
    code: "r23fwf2w3",
    name: "Pink Purse",
    description: "Product Description",
    image: "pink-purse.jpg",
    price: 110,
    category: "Accessories",
    quantity: 0,
    inventoryStatus: "OUTOFSTOCK",
    rating: 4,
  },
  {
    id: "1021",
    code: "pxpzczo23",
    name: "Purple Band",
    description: "Product Description",
    image: "purple-band.jpg",
    price: 79,
    category: "Fitness",
    quantity: 6,
    inventoryStatus: "LOWSTOCK",
    rating: 3,
  },
  {
    id: "1022",
    code: "2c42cb5cb",
    name: "Purple Gemstone Necklace",
    description: "Product Description",
    image: "purple-gemstone-necklace.jpg",
    price: 45,
    category: "Accessories",
    quantity: 62,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1023",
    code: "5k43kkk23",
    name: "Purple T-Shirt",
    description: "Product Description",
    image: "purple-t-shirt.jpg",
    price: 49,
    category: "Clothing",
    quantity: 2,
    inventoryStatus: "LOWSTOCK",
    rating: 5,
  },
  {
    id: "1024",
    code: "lm2tny2k4",
    name: "Shoes",
    description: "Product Description",
    image: "shoes.jpg",
    price: 64,
    category: "Clothing",
    quantity: 0,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1025",
    code: "nbm5mv45n",
    name: "Sneakers",
    description: "Product Description",
    image: "sneakers.jpg",
    price: 78,
    category: "Clothing",
    quantity: 52,
    inventoryStatus: "INSTOCK",
    rating: 4,
  },
  {
    id: "1026",
    code: "zx23zc42c",
    name: "Teal T-Shirt",
    description: "Product Description",
    image: "teal-t-shirt.jpg",
    price: 49,
    category: "Clothing",
    quantity: 3,
    inventoryStatus: "LOWSTOCK",
    rating: 3,
  },
  {
    id: "1027",
    code: "acvx872gc",
    name: "Yellow Earbuds",
    description: "Product Description",
    image: "yellow-earbuds.jpg",
    price: 89,
    category: "Electronics",
    quantity: 35,
    inventoryStatus: "INSTOCK",
    rating: 3,
  },
  {
    id: "1028",
    code: "tx125ck42",
    name: "Yoga Mat",
    description: "Product Description",
    image: "yoga-mat.jpg",
    price: 20,
    category: "Fitness",
    quantity: 15,
    inventoryStatus: "INSTOCK",
    rating: 5,
  },
  {
    id: "1029",
    code: "gwuby345v",
    name: "Yoga Set",
    description: "Product Description",
    image: "yoga-set.jpg",
    price: 20,
    category: "Fitness",
    quantity: 25,
    inventoryStatus: "INSTOCK",
    rating: 8,
  },
]);

const visible = ref(false);

const newProject = ref({ pages: 1 });

const teams = ref([
  { name: "Équipe A", code: "team-a" },
  { name: "Équipe B", code: "team-b" },
  { name: "Équipe B", code: "team-c" },
  { name: "Équipe D", code: "team-d" },
]);

const value = ref([
  { label: "Indéfini", color: "transparent", value: 48 },
  { label: "À faire", color: "var(--yellow-500)", value: 8 },
  { label: "En cours", color: "var(--orange-500)", value: 24 },
  { label: "À valider", color: "var(--blue-500)", value: 10 },
  { label: "Validé", color: "var(--green-500)", value: 10 },
]);
</script>

<template>
  <div class="flex justify-content-between align-items-center">
    <h1 class="text-primary">Projets</h1>
    <Button
      icon="pi pi-plus"
      rounded
      aria-label="Créer un projet"
      v-tooltip.left="'Créer un projet'"
      @click="visible = true"
    />
    <Dialog
      v-model:visible="visible"
      modal
      header="Créer un projet"
      :style="{ width: '25rem' }"
    >
      <div class="field required">
        <label for="name">Nom du projet</label>
        <InputText id="name" v-model="newProject.name" class="w-full" />
      </div>
      <div class="field required">
        <label for="team">Équipe du projet</label>
        <Dropdown
          v-model="newProject.team"
          :options="teams"
          optionLabel="name"
          placeholder="Sélectionnez une équipe"
          class="w-full"
          id="team"
        />
      </div>
      <div class="field required">
        <label for="pages">Nombre de pages</label>
        <InputNumber
          v-model="newProject.pages"
          inputId="pages"
          class="w-full"
          :min="1"
          aria-describedby="pages-help"
          showButtons
        />
        <small id="pages-help">Vous pouvez ajouter des pages plus tard.</small>
      </div>
      <div class="flex justify-content-end gap-2">
        <Button
          type="button"
          label="Annuler"
          severity="secondary"
          @click="visible = false"
          text
        ></Button>
        <Button type="button" label="Créer" @click="visible = false" />
      </div>
    </Dialog>
  </div>

  <div class="grid">
    <div class="col-3" v-for="(item, idx) in products.slice(0, 12)" :key="idx">
      <Card style="overflow: hidden">
        <template #header>
          <div class="bg-primary-100 p-4">
            <img
              alt="user header"
              :src="`https://primefaces.org/cdn/primevue/images/product/${item.image}`"
              style="aspect-ratio: 210/297; object-fit: cover"
              class="block border-round shadow-1 h-15rem mx-auto"
            />
          </div>
        </template>
        <template #title>{{ item.name }}</template>
        <template #subtitle>
          {{ item.category }}
        </template>
        <template #content>
          <MeterGroup
            :value="value"
            :pt="{
              metercontainer: { class: 'h-1rem' },
              labellist: { class: 'hidden' },
            }"
          />
        </template>
        <template #footer>
          <div class="flex gap-3 justify-content-between">
            <div class="flex gap-2">
              <div class="flex gap-1 align-items-center">
                <i class="pi pi-file text-primary" style="font-size: 1rem"></i>
                68
              </div>
              <div class="flex gap-1 align-items-center">
                <i class="pi pi-link text-primary" style="font-size: 1rem"></i>
                12
              </div>
              <div class="flex gap-1 align-items-center">
                <i
                  class="pi pi-comments text-primary"
                  style="font-size: 1rem"
                ></i>
                45
              </div>
            </div>
            <NuxtLink
              :to="{ name: 'projects-uid', params: { uid: item.code } }"
            >
              <Button
                label="Projet"
                icon="pi pi-angle-right"
                iconPos="right"
                class=""
                outlined
              />
            </NuxtLink>
          </div>
        </template>
      </Card>
    </div>
  </div>

  <Paginator
    :rows="12"
    :totalRecords="120"
    :rowsPerPageOptions="[12, 24, 48]"
    class="my-4"
  ></Paginator>
</template>
