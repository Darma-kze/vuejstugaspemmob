<template>
  <div id="app" class="container">
    <!-- Click Counter -->
    <section class="click-counter">
      <h2>Click Counter</h2>
      <div class="counter-controls">
        <button @click="incrementCounter">Klik Saya</button>
        <button @click="resetCounter">Reset</button>
      </div>
      <p>Jumlah Klik: {{ counter }}</p>
    </section>

    <!-- Box Color Changer -->
    <section class="color-changer">
      <h2>Box Color Changer</h2>
      <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
      <button @click="changeBoxColor">Ubah Warna Kotak</button>
    </section>

    <!-- Image Carousel -->
    <section class="image-carousel">
      <h2>Image Carousel</h2>
      <div class="carousel">
        <button @click="prevImage">Prev</button>
        <img :src="images[currentImageIndex]" alt="carousel image" />
        <button @click="nextImage">Next</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Data untuk Click Counter
      counter: 0,

      // Data untuk Box Color Changer
      boxColor: '#3498db',

      // Data untuk Image Carousel
      images: [
        'https://via.placeholder.com/300x200?text=Image+1',
        'https://via.placeholder.com/300x200?text=Image+2',
        'https://via.placeholder.com/300x200?text=Image+3'
      ],
      currentImageIndex: 0
    };
  },
  methods: {
    // Metode untuk Click Counter
    incrementCounter() {
      this.counter++;
    },
    resetCounter() {
      this.counter = 0;
    },

    // Metode untuk Box Color Changer
    changeBoxColor() {
      const colors = ['#3498db', '#e74c3c', '#2ecc71', '#f1c40f'];
      this.boxColor = colors[Math.floor(Math.random() * colors.length)];
    },

    // Metode untuk Image Carousel
    nextImage() {
      this.currentImageIndex =
        (this.currentImageIndex + 1) % this.images.length;
    },
    prevImage() {
      this.currentImageIndex =
        (this.currentImageIndex - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style scoped>
/* Kontainer Utama */
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}

/* Style untuk Setiap Section */
section {
  margin-bottom: 30px;
  text-align: center;
}

/* Style untuk Click Counter */
.click-counter .counter-controls {
  margin-top: 10px;
}

.click-counter button {
  margin: 0 5px;
}

/* Style untuk Box Color Changer */
.color-changer .color-box {
  width: 150px;
  height: 150px;
  margin: 20px auto;
  border: 1px solid #000;
}

/* Style untuk Image Carousel */
.image-carousel .carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.image-carousel .carousel img {
  width: 300px;
  height: 200px;
  object-fit: cover;
  margin: 0 10px;
}

.image-carousel button {
  margin: 0 10px;
}
</style>
