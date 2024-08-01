<template>
  <v-app>
    <NavApp :laps="laps" />
    <v-main class="custom-main">
      <TimerApp
        :timer="formattedTimer"
        @start="start"
        @stop="stop"
        @reset="reset"
        @laps="lap"
      />
    </v-main>
  </v-app>
</template>

<script>
import NavApp from "./components/NavApp.vue";
import TimerApp from "./components/TimerApp.vue";

export default {
  name: "App",

  components: {
    NavApp,
    TimerApp,
  },

  data() {
    return {
      currentTimer: 0, // Toplam geçen süreyi saniye cinsinden saklar
      timer: null, // setInterval ID'sini saklar
      laps: [], // Lap'ları saklayan bir dizi
    };
  },

  computed: {
    // currentTime'ı HH:MM:SS formatına dönüştürür
    formattedTimer() {
      const hours = Math.floor(this.currentTimer / 3600);
      const minutes = Math.floor((this.currentTimer % 3600) / 60);
      const seconds = this.currentTimer % 60;

      // Saat, dakika ve saniyeleri iki haneli formatta döndürür
      return `${this.pad(hours)}:${this.pad(minutes)}:${this.pad(seconds)}`;
    },
  },

  methods: {
    start() {
      if (!this.timer) {
        // Kronometre çalışmıyorsa, setInterval başlatılır

        this.timer = setInterval(() => {
          // Her saniye currentTime'ı bir artırır
          this.currentTimer++; // Her saniye currentTime'ı bir artırır
        }, 1000); // 1000 ms = 1 saniye
      }
    },

    stop() {
      clearInterval(this.timer); // setInterval'ı temizler
      this.timer = null; // Timer'ı sıfır yerine null yaparak durduruyoruz
    },

    reset() {
      this.stop(); // Kronometreyi durdurur
      this.currentTime = 0; // Zamanı sıfırlar
      this.laps = []; // Lap listesini temizler
    },
    // Şu anki zamanı lap olarak kaydeder
    lap() {
      this.laps.push(this.formattedTimer); // Şu anki zamanı laps dizisine ekler
    },
    // Sayıları belirli bir uzunlukta göstermek için sıfır ekler
    pad(num, size = 2) {
      return String(num).padStart(size, "0");
    },
  },
};
</script>

<style scoped>
.custom-main {
  --v-layout-left: 0px;
  --v-layout-right: 0px;
}
</style>
