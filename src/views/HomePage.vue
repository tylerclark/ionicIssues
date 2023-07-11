<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
        <ion-buttons slot="end">
          <ion-button color="primary" fill="solid" id="main-menu-trigger">
            <svg
              slot="icon-only"
              xmlns="http://www.w3.org/2000/svg"
              class="ionicon"
              viewBox="0 0 512 512"
            >
              <circle cx="256" cy="256" r="48" />
              <circle cx="416" cy="256" r="48" />
              <circle cx="96" cy="256" r="48" />
            </svg>
          </ion-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-popover
        trigger="main-menu-trigger"
        dismissOnSelect="true"
        showBackdrop="false"
        cssClass="menuPopover"
      >
        <app-menu @open-sign-up="openSignup" @open-sign-up-2="openSignup2" />
      </ion-popover>
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
  IonPopover,
} from "@ionic/vue";
import AppMenu from "@/views/AppMenu.vue";
import Signup from "./Signup.vue";

const openSignup = async () => {
  const modal = await modalController.create({
    cssClass: "signinModal",
    component: Signup,
    backdropDismiss: false,
  });
  modal.present();
};

const openSignup2 = async (payload: { name: string; when: Date }) => {
  alert(JSON.stringify(payload));
};
</script>

<style>
.menuPopover {
  --background: green;
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
.ionicon {
  fill: currentColor;
  width: 30px;
}
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
