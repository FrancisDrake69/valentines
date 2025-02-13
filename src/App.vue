
<script setup>

import { ref, onMounted } from 'vue';
import gsap from 'gsap';
// import loveSong from './assets/love-song.mp3'; // Optional music
//https://www.youtube.com/embed/o-MY18URLFM?si=NarHhpP6BqtzW8BC?autoplay=1&mute=1

const message = "Hello My Love! ❤️";
const togetherSince = new Date("2024-11-16"); // Change to your date
const daysTogether = ref(0);
const showFirstOptions = ref(false);
const showLoveMessage = ref(false);
const showAreYouSure = ref(false);
const showAreYouReallySure = ref(false);
const showAreYouReallyReallySure = ref(false);
const showAreYouReallyReallyReallyReallyReallySure = ref(false);
const showAreYouReallyReallyReallyReallyReallyReallySure = ref(false);
const showAreYouReallyReallyReallyReallyReallyReallyReallySure = ref(false);
const showAreYouReallyReallyReallyReallyReallyReallyReallyReallySure = ref(false);
const showNotAnOption = ref(false);

onMounted(() => {
  // Calculate love days
  const now = new Date();
  const diffTime = Math.abs(now - togetherSince);
  daysTogether.value = Math.ceil(diffTime / (1000 * 60 * 60 * 24));

  // Heart animation
  gsap.to('.heart', {
    y: -100,
    opacity: 0,
    repeat: -1,
    stagger: 0.2,
    duration: 2,
    ease: 'power1.inOut'
  });
});

const askValentine = () => {
  showFirstOptions.value = true;
};

const sayYes = () => {
  showLoveMessage.value = true;
  showFirstOptions.value = false;
};

const sayNo = () => {
  showAreYouSure.value = true;
  showFirstOptions.value = false;
};

const confirmNo = () => {
  alert("😭 Nooooo! Try again!"); // You can change this to something more fun!
  showAreYouSure.value = false;
  showAreYouReallySure.value = false;
};


const reconsiderYes = () => {
  showLoveMessage.value = true;
  showAreYouSure.value = false;
};
</script>
<template>
  <v-app class="bg-pink-100">
    <v-container class="d-flex flex-column align-center justify-center min-h-screen text-center py-6 sm:py-8 md:py-12 relative overflow-hidden">
      <!-- Floating Hearts -->
      <div v-for="i in 10" :key="i" class="heart absolute text-red-500 text-xl sm:text-2xl md:text-3xl lg:text-4xl"
           :style="{
             '--random-x': Math.random(),
             '--random-y': Math.random()
           }">
        ❤️
      </div>

      <!-- Title -->
      <v-row justify="center">
        <v-col cols="12">
          <h1 class="display-3 font-weight-bold text-pink-700 romantic-font">
            {{ message }}
          </h1>
        </v-col>
      </v-row>
      <br>

      <!-- Love Counter -->
      <v-row justify="center">
        <v-col cols="12">
          <p class="text-lg sm:text-xl mt-4 text-gray-700 romantic-font">
            We've been together for <strong class="text-red-500 text-2xl sm:text-3xl">{{ daysTogether }}</strong> days! 💑
          </p>
        </v-col>
      </v-row>
      <br>

      <!-- Personal Message -->
      <v-row justify="center">
        <v-col cols="12">
          <p class="text-lg sm:text-xl mt-4 text-gray-700 romantic-font">
            We spent so many amazing moments together!
          </p>
        </v-col>
      </v-row>
      <br>
      <br>

      <!-- Photo Gallery / Video -->
      <v-row justify="center">
        <v-col cols="12" sm="8" md="6">
          <iframe
              class="w-full aspect-video rounded-lg shadow-md"
              src="https://www.youtube.com/embed/o-MY18URLFM?si=NarHhpP6BqtzW8BC?autoplay=1&mute=1"
              frameborder="0">
          </iframe>
        </v-col>
      </v-row>
      <br>

      <!-- Personal Message -->
      <v-row justify="center">
        <v-col cols="12">
          <p class="text-lg sm:text-xl mt-4 text-gray-700 romantic-font">
            You make me feel like the happiest man alive!
          </p>
        </v-col>
      </v-row>

      <br>

      <!-- "Will you be my Valentine?" Button -->
      <v-row justify="center" class="mt-6">
        <v-col cols="12">
          <v-btn
              v-if="!showFirstOptions && !showLoveMessage && !showAreYouSure"
              @click="askValentine"
              class="ma-2 py-3 px-6 sm:px-8 sm:py-4 gradient-background"
              color="deep-purple accent-4" dark
              :style="{ borderRadius: '12px' }"
          >
            💌 Will you be my Valentine? 💌
          </v-btn>
        </v-col>
      </v-row>

      <br>
      <br>
      <!-- First Yes/No Options -->

      <v-row v-if = "showFirstOptions" justify="center" class="mt-6 d-flex justify-center">
        <v-col cols="12" sm="5" md="4" class="d-flex justify-center">
          <v-btn @click="sayYes"
                 class="ma-2 py-3 px-8 bg-gradient-to-r from-green-500 via-teal-500 to-green-600"
                 color="green" dark large rounded>
            ✅ Yes!
          </v-btn>
        </v-col>

        <v-col cols="12" sm="5" md="4" class="d-flex justify-center">
          <v-btn @click="sayNo"
                 class="ma-2 py-3 px-8 bg-gradient-to-r from-gray-500 via-gray-600 to-gray-700"
                 color="gray" dark large rounded>
            ❌ No...
          </v-btn>
        </v-col>
      </v-row>

      <br>

      <!-- "Yay! I Love You!" Message -->
      <v-row v-if="showLoveMessage" justify="center" class="mt-6">
        <v-col cols="12">
          <p class="display-1 text-red-500 font-weight-bold romantic-font">
            Yayyyyyyyyyyyyy! 😍💖
          </p>
        </v-col>

        <br>

        <div>
          <img src= "https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWZyZzk0cnE1YzlzbHFlbWZ3a2w1MDBnMTBiNHJjaWo2YXJheXNmNiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/NxC8VtyxqhMtpLoEEN/giphy.gif" />
        </div>

      </v-row>

      <br>

      <!-- "Are you sure?" Prompt -->
      <v-row v-if="showAreYouSure" justify="center" class="mt-4">
        <v-col cols="12">
          <p class="text-xl text-gray-700 romantic-font">Are you sure? 😢</p>
        </v-col>
        <v-col cols="12" sm="6" md="4" class="d-flex justify-center mt-4">
          <v-btn @click="reconsiderYes" class="ma-2 py-3 px-8 bg-green-500" color="green" dark large rounded>
            ❤️ Okay, Yes!
          </v-btn>
          <v-btn @click="confirmNo" class="ma-2 py-3 px-8 bg-gray-500" color="gray" dark large rounded>
            ❌ Yes, I'm Sure...
          </v-btn>
        </v-col>
      </v-row>

      <!-- More Yes/No Options After "Are You Sure?" -->
      <v-row v-if="showAreYouReallySure" justify="center" class="mt-4">
        <v-col cols="12">
          <p class="text-xl text-gray-700 romantic-font">Are you really sure? 🤔</p>
        </v-col>
        <v-col cols="12" sm="6" md="4" class="d-flex justify-center mt-4">
          <v-btn @click="reconsiderReallyYes" class="ma-2 py-3 px-8 bg-blue-500" color="blue" dark large rounded>
            ❤️ Okay, I guess!
          </v-btn>
          <v-btn @click="confirmReallyNo" class="ma-2 py-3 px-8 bg-red-500" color="red" dark large rounded>
            ❌ I'm absolutely sure!
          </v-btn>
        </v-col>
      </v-row>

      <!-- Repeat for each subsequent state (if needed) -->
    </v-container>
  </v-app>
</template>

<style scoped>
.romantic-font {
  font-family: 'Playfair Display', serif;
}
.heart {
  position: absolute;
  animation: float 6s ease-in-out infinite;
}

@keyframes float {
  0% {
    transform: translateY(0) scale(1);
  }
  50% {
    transform: translateY(-300px) scale(1.2);
  }
  100% {
    transform: translateY(0) scale(1);
  }
}

.heart {
  left: calc(100% * var(--random-x));
  top: calc(100% * var(--random-y));
}
</style>


