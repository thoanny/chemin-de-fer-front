<template>
  <div class="flex justify-content-between align-items-center">
    <h1 class="text-primary">Mon compte</h1>
  </div>

  <div class="grid">
    <div class="col-4">
      <Card>
        <template #title>Équipes</template>
        <template #subtitle>3/50 membres</template>
        <template #content>
          <ProgressBar :value="15" />
        </template>
      </Card>
    </div>
    <div class="col-4">
      <Card>
        <template #title>Projets</template>
        <template #subtitle>5/10 actifs</template>
        <template #content>
          <ProgressBar :value="50" />
        </template>
      </Card>
    </div>
    <div class="col-4">
      <Card>
        <template #title>Stockage</template>
        <template #subtitle>15/250 Mo</template>
        <template #content>
          <ProgressBar :value="6" />
        </template>
      </Card>
    </div>
  </div>
</template>
