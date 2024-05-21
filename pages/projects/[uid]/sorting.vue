<script setup>
import { useDragAndDrop } from "@formkit/drag-and-drop/vue";
import { multiDrag, selections } from "@formkit/drag-and-drop";

const route = useRoute();
const ASPECT_RATIO = "210/297";

const products = ref([
  {
    id: "1000",
    code: "f230fh0g3",
    name: "Bamboo Watch",
    page: 1,
  },
  {
    id: "1001",
    code: "nvklal433",
    name: "Black Watch",
    page: 2,
  },
  {
    id: "1002",
    code: "zz21cz3c1",
    name: "Blue Band",
    page: 3,
  },
  {
    id: "1003",
    code: "244wgerg2",
    name: "Blue T-Shirt",
    page: 4,
  },
  {
    id: "1004",
    code: "h456wer53",
    name: "Bracelet",
    page: 5,
  },
  {
    id: "1005",
    code: "av2231fwg",
    name: "Brown Purse",
    page: 6,
  },
  {
    id: "1006",
    code: "bib36pfvm",
    name: "Chakra Bracelet",
    page: 7,
  },
  {
    id: "1007",
    code: "mbvjkgip5",
    name: "Galaxy Earrings",
    page: 8,
  },
  {
    id: "1008",
    code: "vbb124btr",
    name: "Game Controller",
    page: 9,
  },
  {
    id: "1009",
    code: "cm230f032",
    name: "Gaming Set",
    page: 10,
  },
  {
    id: "1010",
    code: "plb34234v",
    name: "Gold Phone Case",
    page: 11,
  },
  {
    id: "1011",
    code: "4920nnc2d",
    name: "Green Earbuds",
    page: 12,
  },
  {
    id: "1012",
    code: "250vm23cc",
    name: "Green T-Shirt",
    page: 13,
  },
  {
    id: "1013",
    code: "fldsmn31b",
    name: "Grey T-Shirt",
    page: 14,
  },
  {
    id: "1014",
    code: "waas1x2as",
    name: "Headphones",
    page: 15,
  },
]);

const [parent, tapes] = useDragAndDrop(products, {
  draggingClass: "dragging",
  dropZoneClass: "dropzone",
  plugins: [
    multiDrag({
      plugins: [
        selections({
          selectedClass: "selected",
        }),
      ],
    }),
  ],
});
</script>

<template>
  <div class="flex">
    <h1 class="text-primary">Organiser les pages</h1>
  </div>

  <Card>
    <template #content>
      <div
        ref="parent"
        class="flex gap-3 flex-wrap overflow-hidden justify-content-center"
      >
        <div
          v-for="(page, idx) in tapes"
          :key="page.id"
          class="page"
          :style="`aspect-ratio: ${ASPECT_RATIO}`"
        >
          <img
            :src="`https://picsum.photos/id/1${page.page}/360/510`"
            class="block w-full h-full"
            style="object-fit: cover"
            alt=""
          />
          <span class="overlay">
            <span>
              {{ page.name }}
            </span>
          </span>
          <span
            class="absolute border-round-sm -bottom-2px bg-primary px-1 py-1 text-xs -right-2px"
            >{{ idx }}</span
          >
        </div>
      </div>
    </template>
    <template #footer>
      <div class="flex gap-3 mt-1">
        <Button
          label="Annuler"
          severity="secondary"
          outlined
          class="w-full"
          @click="
            navigateTo({
              name: 'projects-uid',
              params: { uid: route.params.uid },
            })
          "
        />
        <Button label="Enregistrer" class="w-full" />
      </div>
    </template>
  </Card>
</template>

<style scoped>
.page {
  width: 8rem;
  height: auto;
  border: 2px solid var(--primary-color);
  flex-shrink: 0;
  border-radius: var(--border-radius);
  overflow: hidden;
  position: relative;
  outline: none;
}

.overlay {
  position: absolute;
  display: flex;
  width: 100%;
  height: 100%;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 0.5rem;
  background: rgba(0, 0, 0, 0.5);
  color: white;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 1);
  font-size: 0.85rem;
  top: 0;
}

.page.selected .overlay {
  background: color-mix(in srgb, var(--primary-color), transparent 50%);
}

.dragging .overlay {
  background: red !important;
}

.dropzone .overlay {
  border-color: green !important;
}
</style>
