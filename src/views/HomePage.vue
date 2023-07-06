<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
        <ion-buttons slot="end">
          <ion-button @click="openMenu">
            <ion-icon slot="icon-only" :icon="ellipsisHorizontal"></ion-icon>
          </ion-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <div id="container">
        <strong>Ready to create an app?</strong>
        <p>
          Start with Ionic
          <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components"
            >UI Components</a
          >
        </p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import {
  popoverController,
  modalController,
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
  IonButtons,
  IonButton,
  IonIcon,
} from "@ionic/vue";
import { ellipsisHorizontal } from "ionicons/icons";
import Menu from "./Menu.vue";
import Signup from "./Signup.vue";

const openSignup = async () => {
  console.log("home:openSignup");
  const modal = await modalController.create({
    cssClass: "signinModal",
    component: Signup,
    backdropDismiss: false,
  });
  modal.present();
};

const openMenu = async (ev: Event) => {
  const popover = await popoverController.create({
    component: Menu,
    cssClass: "menuPopover",
    event: ev,
    dismissOnSelect: true,
    showBackdrop: false,
    componentProps: {
      openSignup: openSignup,
    },
  });
  await popover.present();
};
</script>

<style>
.menuPopover {
  --background: orange;
  --color: white;
}
.signinModal {
  --height: fit-content;
  --border-radius: 10px;
  --margin: 0 20px;
  --width: calc(100% - 40px);
  --max-width: 400px;
  --backdrop-opacity: 0.8;
  margin-top: -290px;
}
</style>

<style scoped>
#container {
  text-align: center;

  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
