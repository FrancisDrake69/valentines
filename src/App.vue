

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
};

const reconsiderYes = () => {
  showLoveMessage.value = true;
  showAreYouSure.value = false;
};
</script>

<template>
  <div class="min-h-screen bg-pink-100 flex flex-col items-center justify-center text-center p-6 sm:p-8 md:p-12 relative overflow-hidden">
    <!-- Floating Hearts -->
    <div v-for="i in 10" :key="i" class="heart absolute text-red-500 text-xl sm:text-2xl md:text-3xl lg:text-4xl"
         :style="{ left: `${Math.random() * 100}%`, top: `${Math.random() * 100}%` }">
      ❤️
    </div>

    <!-- Title -->
    <h1 class="text-3xl sm:text-4xl md:text-6xl font-bold text-pink-700 leading-tight">
      {{ message }}
    </h1>

    <br>

    <!-- Love Counter -->
    <p class="text-lg sm:text-xl mt-4 text-gray-700">
      We've been together for <strong class="text-red-500 text-2xl sm:text-3xl">{{ daysTogether }}</strong> days! 💑
    </p>

    <br>

    <!-- Personal Message -->
    <p class="text-lg sm:text-xl mt-4 text-gray-700">
      You make me feel like the happiest man alive!
    </p>

    <br>

    <p class="text-lg sm:text-xl mt-4 text-gray-700">
      We've spent so many beautiful moments together:
    </p>


    <!-- Photo Gallery / Video -->
    <div class="p-4 flex justify-center">
      <iframe
          class="w-full sm:w-2/3 md:w-1/2 aspect-video rounded-lg shadow-md"
          src="https://www.youtube.com/embed/o-MY18URLFM?si=NarHhpP6BqtzW8BC?autoplay=1&mute=1"
          frameborder="0">
      </iframe>
    </div>

    <br>

    <!-- "Will you be my Valentine?" Button -->
    <div class="flex justify-center">
      <button
          v-if="!showFirstOptions && !showLoveMessage && !showAreYouSure"
          @click="askValentine"
          class="valentine-button mt-6 px-6 py-3 sm:px-8 sm:py-4 bg-gradient-to-r from-red-500 via-pink-500 to-red-600 text-white text-lg font-semibold text-center"
      >
        💌 Do you want to be my Valentine? 💌
      </button>
    </div>

    <!-- First Yes/No Options -->
    <div v-if="showFirstOptions" class="mt-6 flex gap-6 justify-center">
      <button @click="sayYes"
              class="px-8 py-4 bg-gradient-to-r from-green-500 via-teal-500 to-green-600 text-white text-lg font-semibold rounded-full shadow-xl transform transition-all hover:scale-105 hover:shadow-2xl focus:outline-none focus:ring-2 focus:ring-green-300 focus:ring-opacity-50">
        ✅ Yes!
      </button>
      <button @click="sayNo"
              class="px-8 py-4 bg-gradient-to-r from-gray-500 via-gray-600 to-gray-700 text-white text-lg font-semibold rounded-full shadow-xl transform transition-all hover:scale-105 hover:shadow-2xl focus:outline-none focus:ring-2 focus:ring-gray-300 focus:ring-opacity-50">
        ❌ No...
      </button>
    </div>

    <!-- "Yay! I Love You!" Message -->
    <div v-if="showLoveMessage" class="mt-6 flex gap-6 justify-center">
      <p class="text-3xl text-red-500 mt-6 font-bold">Yay! I love you! 😍💖</p>
      <img
          src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWZyZzk0cnE1YzlzbHFlbWZ3a2w1MDBnMTBiNHJjaWo2YXJheXNmNiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/NxC8VtyxqhMtpLoEEN/giphy.gif"
          alt="Valentine's Day Wallpaper"
          class="w-full sm:w-2/3 md:w-1/2 lg:w-1/3 rounded-lg shadow-xl object-cover"
      />
    </div>

    <!-- "Are you sure?" Prompt -->
    <div v-if="showAreYouSure" class="mt-4 flex flex-col items-center">
      <p class="text-xl text-gray-700">Are you sure? 😢</p>
      <div class="mt-4 flex gap-4">
        <button @click="reconsiderYes"
                class="px-6 py-3 bg-green-500 text-white rounded-full shadow-md hover:bg-green-600 transition">
          ❤️ Okay, Yes!
        </button>
        <button @click="confirmNo"
                class="px-6 py-3 bg-gray-500 text-white rounded-full shadow-md hover:bg-gray-600 transition">
          ❌ Yes, I'm Sure...
        </button>
      </div>
    </div>
  </div>
</template>


<style scoped>
.heart {
  position: absolute;
  animation: float 5s infinite;
}
</style>

