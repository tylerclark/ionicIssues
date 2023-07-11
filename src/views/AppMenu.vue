<template>
  <ion-content>
    <ion-list>
      <ion-item :button="true" :detail="false" @click="openSignup"
        >Menu option 1</ion-item
      >
      <ion-item :button="true" :detail="false" @click="openSignup2"
        >Menu option 2</ion-item
      >
      <ion-item :button="true" :detail="false" @click="openSignup"
        >Menu option 3</ion-item
      >
    </ion-list>
  </ion-content>
</template>

<script setup lang="ts">
import { IonContent, IonItem, IonList } from "@ionic/vue";

const emits = defineEmits<{
  (event: "open-sign-up"): void;
  (event: "open-sign-up-2", { name, when }: { name: string; when: Date }): void;
}>();

const openSignup = () => {
  emits("open-sign-up");
};

const openSignup2 = () => {
  emits("open-sign-up-2", { name: "aaron", when: new Date() });
};
</script>

<style scoped>
ion-item {
  --background: orange;
  --color: white;
  --inner-border-width: 0;
}
</style>
