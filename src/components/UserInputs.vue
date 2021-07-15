<template>
  <div class="grid justify-center">
    <form action="" class="min-w-full w-72 mt-10" @submit.prevent="addDevice">
      <p class="title text-center font-bold text-2xl my-4">Your Home</p>

      <!-- DEVICE -->
      <label for="name" class="my-2 block text-sm font-medium text-gray-700">Device</label>
      <div class="relative flex w-full flex-wrap items-stretch mb-3">
        <input
          v-model="devices.device"
          type="text"
          placeholder="Enter your device"
          class="px-3 py-3 placeholder-blueGray-300 text-blueGray-600 relative bg-white rounded text-sm border border-blueGray-300 outline-none focus:outline-none focus:ring w-full pr-10"
        />
        <span
          class="z-10 h-full leading-snug font-normal absolute text-center text-blueGray-300 bg-transparent rounded text-base items-center justify-center w-8 right-0 pr-3 py-3 "
        >
          <img src="@/assets/microwave.png" alt="" />
        </span>
      </div>
      <!-- BUYING PRICE -->
      <label for="name" class="my-2 block text-sm font-medium text-gray-700">Buying Price</label>
      <div class="relative flex w-full flex-wrap items-stretch mb-3">
        <input
          v-model="devices.buyingPrice"
          type="text"
          placeholder="$300"
          class="px-3 py-3 placeholder-blueGray-300 text-blueGray-600 relative bg-white rounded text-sm border border-blueGray-300 outline-none focus:outline-none focus:ring w-full pr-10"
        />
        <span
          class="z-10 h-full leading-snug font-normal absolute text-center text-blueGray-300 bg-transparent rounded text-base items-center justify-center w-8 right-0 pr-3 py-3 "
        >
          <img src="@/assets/money-bag.png" alt="" />
        </span>
      </div>
      <!-- AVERAGE LIFESPAN -->
      <label for="name" class="my-2 block text-sm font-medium text-gray-700"
        >Average Lifespan</label
      >
      <div class="relative flex w-full flex-wrap items-stretch mb-3">
        <input
          v-model="devices.averageLifespan"
          type="text"
          placeholder="e.g. 7"
          class="px-3 py-3 placeholder-blueGray-300 text-blueGray-600 relative bg-white rounded text-sm border border-blueGray-300 outline-none focus:outline-none focus:ring w-full pr-10"
        />
        <span
          class="z-10 h-full leading-snug font-normal absolute text-center text-blueGray-300 bg-transparent rounded text-base items-center justify-center w-8 right-0 pr-3 py-3 "
        >
          <img src="@/assets/stopwatch.png" alt="" />
        </span>
      </div>
      <!-- YEARS IN USE -->
      <label for="name" class="my-2 block text-sm font-medium text-gray-700">Years in use</label>
      <div class="relative flex w-full flex-wrap items-stretch mb-3">
        <input
          v-model="devices.yearsInUse"
          type="text"
          placeholder="e.g. 2"
          class="px-3 py-3 placeholder-blueGray-300 text-blueGray-600 relative bg-white rounded text-sm border border-blueGray-300 outline-none focus:outline-none focus:ring w-full pr-10"
        />
        <span
          class="z-10 h-full leading-snug font-normal absolute text-center text-blueGray-300 bg-transparent rounded text-base items-center justify-center w-8 right-0 pr-3 py-3 "
        >
          <img src="@/assets/stopwatch.png" alt="" />
        </span>
      </div>

      <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded w-full">
        Add
      </button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      devices: [
        {
          device: '',
          buyingPrice: null,
          averageLifespan: null,
          yearsInUse: null,
        },
      ],
    };
  },
  methods: {
    async addDevice() {
      await axios
        .post('http://localhost:3000/api/devices', {
          device: this.devices.device,
          buyingPrice: this.devices.buyingPrice,
          averageLifespan: this.devices.averageLifespan,
          yearsInUse: this.devices.yearsInUse,
        })
        .catch((err) => console.error(err))
        .then(() => {
          this.devices = [];
        });
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Architects+Daughter&display=swap');

p {
  font-family: 'Architects Daughter', cursive;
}
</style>
