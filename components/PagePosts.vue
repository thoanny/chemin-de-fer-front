<script setup>
const visible = ref(false);
</script>

<template>
  <!-- Posts header -->
  <div class="flex gap-2 align-items-center">
    <span class="pi pi-align-left text-primary text-xl"></span>
    <h3 class="text-2xl">Articles</h3>
    <Button
      icon="pi pi-plus"
      rounded
      size="small"
      class="h-2rem w-2rem"
      @click="visible = true"
    />

    <Dialog
      v-model:visible="visible"
      modal
      header="Ajouter un article"
      :style="{ width: '30rem' }"
    >
      <div class="field">
        <label for="post_title" class="font-semibold">
          Titre de l'article
        </label>
        <InputText id="post_title" class="w-full" autocomplete="off" />
      </div>
      <div class="field">
        <label for="post_url" class="font-semibold">
          Adresse de l'article
        </label>
        <InputText type="url" id="post_url" class="w-full" autocomplete="off" />
      </div>

      <div class="flex justify-content-end gap-2">
        <Button
          type="button"
          label="Annuler"
          severity="secondary"
          @click="visible = false"
        ></Button>
        <Button
          type="button"
          label="Enregistrer"
          @click="visible = false"
        ></Button>
      </div>
    </Dialog>
  </div>

  <!-- Posts list -->

  <div class="flex flex-column gap-2">
    <div class="border-round border-1 surface-border p-3 surface-card">
      <div class="flex gap-4 align-items-center justify-content-between">
        <div class="flex flex-column gap-1">
          <a href="#!" class="text-primary font-bold">Nom de l'article</a>
          <div class="text-sm">Relu et corrigé par&nbsp;: Anthony, Eliette</div>
        </div>
        <div class="flex gap-2">
          <Button
            icon="pi pi-thumbs-up"
            severity="success"
            v-tooltip="'Relu et corrigé'"
          />
          <Button icon="pi pi-pencil" v-tooltip="'Modifier l\'article'" />
        </div>
      </div>
    </div>
    <div class="border-round border-1 surface-border p-3 surface-card">
      <div class="flex gap-4 align-items-center justify-content-between">
        <div class="flex flex-column gap-1">
          <a href="#!" class="text-primary font-bold">Nom de l'article</a>
        </div>
        <div class="flex gap-2">
          <Button
            icon="pi pi-thumbs-up"
            severity="success"
            v-tooltip="'Relu et corrigé'"
          />
          <Button icon="pi pi-pencil" v-tooltip="'Modifier l\'article'" />
        </div>
      </div>
    </div>
  </div>
</template>
