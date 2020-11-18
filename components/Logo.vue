<template>
  <div :class="$style.border">
    <div :class="$style.image">
      <!-- <img src="~/assets/picture.png" alt="Your Logo" :class="$style.logo" /> -->
    </div>
  </div>
</template>

<style lang="scss" module>
.border {
  width: 210px;
  height: 210px;
  margin-left: auto;
  margin-right: auto;
  border: 5px solid #34b0fc;
  border-radius: 50%;
}
.image {
  width: 200px;
  height: 200px;
  border: 5px solid white;
  background-image: url('../assets/picture-beautified-2.jpg');
  background-size: 285px;
  border-radius: 50%;
  overflow: hidden;
  background-position-y: -20px;
  background-position-x: -45px;
}
.logo {
  border: 5px solid black;
  width: 200px;
  border-radius: 1500px;
  @apply mx-auto;
  animation: 1s appear;
}

@keyframes appear {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
