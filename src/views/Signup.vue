<template>
  <ion-header>
    <ion-toolbar>
      <ion-title>Sign Up or Sign In</ion-title>
      <ion-buttons slot="end">
        <ion-button class="closeButton" fill="clear" color="dark" @click="closeModal">
          <ion-icon slot="icon-only" :icon="closeCircle"></ion-icon>
        </ion-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>
  <div class="ion-padding">
    <div id="socials">
      <div>
        <ion-icon :icon="logoGoogle" size="large"></ion-icon>
      </div>
      <div>
        <ion-icon :icon="logoApple" size="large"></ion-icon>
      </div>
    </div>
    <div id="or">
      <div></div>
      <div>or</div>
      <div></div>
    </div>
    <div>
      <form @v-on:submit.prevent>
        <ion-input
          class="ion-margin-top ion-margin-bottom"
          label="Email"
          label-placement="floating"
          type="email"
          name="email"
          autocomplete="username"
          spellcheck="false"
          autocorrect="on"
          placeholder="email@domain.com"
          inputmode="email"
        />
        <ion-button expand="block">Continue</ion-button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { defineComponent, nextTick } from "vue";
import { closeCircle, logoGoogle, logoApple } from "ionicons/icons";

import {
  modalController,
  alertController,
  IonCheckbox,
  IonButton,
  IonSpinner,
  IonToolbar,
  IonHeader,
  IonButtons,
  IonTitle,
  IonBackButton,
  IonIcon,
  IonInput,
} from "@ionic/vue";

const closeModal = () => {
  return modalController.dismiss();
};
</script>

<style scoped>
ion-input {
  --background: #f5f5f5;
  --padding-start: 10px;
}
#socials {
  display: flex;
  flex-direction: row;
  margin-top: 10px;
  margin-bottom: 20px;
  gap: 10px;
}
#socials > div {
  flex: 1;
  text-align: center;
  border: 1px #ddd solid;
  height: 80px;
  display: grid;
  place-items: center;
  border-radius: 10px;
}
#or {
  display: flex;
  flex-direction: row;
  margin-top: 20px;
}
#or > div:nth-child(1) {
  margin-top: 9px;
  flex: 1;
  border-top: 1px #ddd solid;
}
#or > div:nth-child(2) {
  padding: 0 20px;
}
#or > div:nth-child(3) {
  margin-top: 9px;
  flex: 1;
  border-top: 1px #ddd solid;
}
</style>
