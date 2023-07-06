<template>
  <ion-content>
    <ion-list>
      <ion-item :button="true" :detail="false" @click="openSignup">Menu option 1</ion-item>
      <ion-item :button="true" :detail="false" @click="openSignup">Menu option 2</ion-item>
      <ion-item :button="true" :detail="false" @click="openSignup">Menu option 3</ion-item>
    </ion-list>
  </ion-content>
</template>

<script setup>
import { defineProps } from "vue";
import { IonContent, IonItem, IonList } from "@ionic/vue";

const props = defineProps({
  openSignup: Function,
});

const openSignup = () => {
  console.log("menu:openSignup");
  props.openSignup();
};
</script>

<style scoped>
ion-item {
  --background: orange;
  --color: white;
  --inner-border-width: 0;
}
</style>
