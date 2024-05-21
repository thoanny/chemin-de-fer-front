<script setup>
const visible = ref(false);
</script>

<template>
  <!-- Comment header -->
  <div class="flex gap-2 align-items-center">
    <span class="pi pi-comments text-primary text-xl"></span>
    <h3 class="text-2xl">Commentaires</h3>
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
      header="Ajouter un commentaire"
      :style="{ width: '30rem' }"
    >
      <div class="field">
        <label for="post_comment" class="font-semibold"> Commentaire </label>
        <Textarea
          autoResize
          rows="5"
          cols="30"
          class="w-full"
          id="post_comment"
          autofocus
        />
      </div>

      <div class="flex justify-content-end gap-2">
        <Button
          type="button"
          label="Annuler"
          severity="secondary"
          @click="visible = false"
        ></Button>
        <Button type="button" label="Ajouter" @click="visible = false"></Button>
      </div>
    </Dialog>
  </div>

  <!-- Comments list -->

  <div class="border-round border-1 surface-border p-3 surface-card mb-3">
    <div class="flex mb-3 gap-3 align-items-center">
      <Avatar
        image="https://gravatar.com/avatar/423de53e1cbf220c85b4ee13b4db1dad3289c1f2257a1783dfd439a758be45c1?d=mp"
        size="large"
        class="bg-primary border-round overflow-hidden"
      />
      <div class="flex flex-column gap-1">
        <div class="font-bold">Anthony</div>
        <div class="text-sm">18 mai 2024 18:00</div>
      </div>
    </div>
    <div>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris id justo
      pulvinar, consectetur enim id, venenatis ex. Maecenas vitae efficitur
      nisi. Donec dolor risus, blandit eget sodales sed, aliquam eget enim.
      Quisque dictum, elit sit amet hendrerit rhoncus, mauris elit blandit
      velit, a mollis urna ipsum ac magna. Duis a fringilla ligula, at ultricies
      erat. Sed in quam sit amet tortor posuere rutrum sit amet ut ex. Vivamus
      eget odio vulputate, dapibus metus et, commodo urna.
    </div>
    <div class="flex justify-content-between mt-3">
      <Button
        label="Répondre"
        icon="pi pi-reply"
        size="small"
        @click="visible = true"
      />
      <Button
        label="Fermer"
        icon="pi pi-check-circle"
        size="small"
        severity="success"
      />
    </div>
  </div>

  <div class="border-round border-1 surface-border p-3 surface-card ml-6 mb-3">
    <div class="flex mb-3 gap-3 align-items-center">
      <Avatar
        image="https://gravatar.com/avatar/8b3a223420377b4acb87d02e10d5665e3adb0dff3f6aeeda11461dcec9265744?d=mp"
        class="bg-primary border-round overflow-hidden"
        size="large"
      />
      <div class="flex flex-column gap-1">
        <div class="font-bold">Eliette</div>
        <div class="text-sm">18 mai 2024 18:02</div>
      </div>
    </div>
    <div>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris id justo
      pulvinar, consectetur enim id, venenatis ex.
    </div>
    <div class="flex justify-content-end mt-3">
      <Button
        label="Fermer"
        icon="pi pi-check-circle"
        size="small"
        severity="success"
      />
    </div>
  </div>
</template>
