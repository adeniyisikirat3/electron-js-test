<template>
  <div class="home" v-if="ready">
    <div class="card">
      <canvas id="name"></canvas>
      Stanley Masinde
    </div>
    <div class="card">
      <canvas id="tezos"></canvas>
      Tezos
    </div>
    <div class="card">
      <canvas id="burst"></canvas>
      Burst
    </div>
    <div class="card">
      <canvas id="cardano"></canvas>
      Burst
    </div>
  </div>
</template>

<script>
import QRCode from "qrcode";
export default {
  data() {
    return {
      ready: true,
      name: "Stanley Masinde",
      tezos: "0",
      burst: "0",
      cardano: "0"
    };
  },
  methods: {
    init() {
      QRCode.toCanvas(document.getElementById("name"), this.name);
      QRCode.toCanvas(document.getElementById("tezos"), this.tezos);
      QRCode.toCanvas(document.getElementById("burst"), this.burst);
      QRCode.toCanvas(document.getElementById("cardano"), this.cardano);
    }
  },
  mounted() {
    this.init();
    setInterval(() => {
      this.name =
        Math.random()
          .toString(36)
          .substring(2, 15) +
        Math.random()
          .toString(36)
          .substring(2, 15);
      this.ready = false;
      this.ready = true;
      this.init();
    }, 5000);
  }
};
</script>
