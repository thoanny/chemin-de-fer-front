<script setup>
const usersRolesToggle = ref(false);
const nodes = ref([
  {
    key: "0",
    data: {
      name: "ANSFL",
    },
    children: [
      {
        key: "0-0",
        data: {
          name: "Anthony Destenay",
          size: "Propriétaire",
        },
      },
      {
        key: "0-1",
        data: {
          name: "Jane Doe",
          size: "Admin",
        },
      },
      {
        key: "0-2",
        data: {
          name: "John Doe",
          size: "Membre",
        },
      },
    ],
  },
]);
</script>

<template>
  <div class="flex justify-content-between align-items-center">
    <h1 class="text-primary">
      Équipes
      <span
        class="pi pi-question-circle cursor-pointer text-xl"
        @click="usersRolesToggle = !usersRolesToggle"
      ></span>
    </h1>
    <Button
      icon="pi pi-plus"
      v-tooltip.left="'Créer une équipe'"
      arial-label="Créer une équipe"
      rounded
    />
  </div>

  <Card
    class="my-4 overflow-hidden"
    :pt="{ body: { class: 'p-0' } }"
    v-show="usersRolesToggle"
  >
    <template #content>
      <div
        class="p-datatable p-component p-datatable-responsive-scroll border-round overflow-hidden"
      >
        <div class="p-datatable-wrapper">
          <table class="p-datatable-table">
            <thead class="p-datatable-thead">
              <tr>
                <th>
                  <div class="p-column-header-content">
                    <span class="p-column-title">Autorisations</span>
                  </div>
                </th>
                <th>
                  <div class="p-column-header-content justify-content-center">
                    <span class="p-column-title">Membre</span>
                  </div>
                </th>
                <th>
                  <div class="p-column-header-content justify-content-center">
                    <span class="p-column-title">Admin</span>
                  </div>
                </th>
                <th>
                  <div class="p-column-header-content justify-content-center">
                    <span class="p-column-title">Propriétaire</span>
                  </div>
                </th>
              </tr>
            </thead>
            <tbody class="p-datatable-tbody">
              <tr>
                <td colspan="4" class="font-bold text-gray-500">Projets</td>
              </tr>
              <tr>
                <td>Créer des projets</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Archiver les projets</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Supprimer les projets</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td colspan="4" class="font-bold text-gray-500">Pages</td>
              </tr>
              <tr>
                <td>Ajouter des pages</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Modifier le nom des pages</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Changer le statut des pages</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Vérouiller/déverouiller les pages</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Supprimer les pages</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td colspan="4" class="font-bold text-gray-500">Articles</td>
              </tr>
              <tr>
                <td>Ajouter des articles</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Modifier les articles</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Supprimer les articles</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Valider les relectures des articles</td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td colspan="4" class="font-bold text-gray-500">
                  Commentaires
                </td>
              </tr>
              <tr>
                <td>Ajouter des commentaires</td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
              <tr>
                <td>Fermer les commentaires</td>
                <td class="text-center">
                  <span class="pi pi-times-circle text-red-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
                <td class="text-center">
                  <span class="pi pi-check-circle text-green-500"></span>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </template>
  </Card>

  <Card class="overflow-hidden my-4" :pt="{ body: { class: 'p-0' } }">
    <template #content>
      <TreeTable :value="nodes" class="p-treetable-small">
        <Column field="name" header="Nom" class="font-bold" expander></Column>
        <Column field="size" header="Rôle"></Column>
        <Column headerStyle="width: 8rem" field="name">
          <template #body="{ node }">
            <div class="flex gap-2" v-if="!node.children">
              <Button
                type="button"
                icon="pi pi-user-edit"
                @click="console.log('Delete node:', node.key)"
                arial-label="Modifier l'accès"
                v-tooltip.left="'Modifier l\'accès'"
                rounded
                outlined
              />
              <Button
                type="button"
                icon="pi pi-user-minus"
                @click="console.log('Add user to node:', node.key)"
                arial-label="Supprimer l'accès"
                v-tooltip.left="'Supprimer l\'accès'"
                severity="danger"
                rounded
                outlined
              />
            </div>
            <div class="flex gap-2" v-else>
              <Button
                type="button"
                icon="pi pi-pencil"
                @click="console.log('Delete node:', node.key)"
                arial-label="Modifier le nom"
                v-tooltip.left="'Modifier le nom'"
                rounded
                outlined
              />
              <Button
                type="button"
                icon="pi pi-user-plus"
                @click="console.log('Add user to node:', node.key)"
                arial-label="Ajouter à l'équipe"
                v-tooltip.left="'Ajouter à l\'équipe'"
                rounded
                outlined
              />
            </div>
          </template>
        </Column>
      </TreeTable>
    </template>
  </Card>
</template>
