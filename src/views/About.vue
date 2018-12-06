<template>
  <div class="about">
    <ion-header>
      <ion-toolbar>
        <ion-title>Image</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-img :src="imageSrc"></ion-img>
    <ion-button @click="$router.go(-1)">Back</ion-button>
  </div>
</template>

<script>
export default {
  props: ['imageSrc']
}
</script>

