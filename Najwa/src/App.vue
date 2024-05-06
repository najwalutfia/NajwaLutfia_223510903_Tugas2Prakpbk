<template>
  <div class="NAJWA">
    <h1>PET HOTEL NAJWA</h1>
    <div class="album">
      <!-- Tambahkan gambar-gambar album di sini -->
      <img src="./src/assets/black1.jpg" alt="kucing black" style="width: 100px; height: 100px;">
      <img src="./src/assets/abuabu.jpg" alt="kucing abu abu" style="width: 100px; height: 100px;">
      <img src="./src/assets/white.jpg" alt="kucing putih" style="width: 100px; height: 100px;">
    </div>
    <p>Email:</p>
    <!-- Input email -->
    <input type="text" v-model="email" :style="{ 'background-color': buttonBackgroundColor }" @blur="validateEmail">
    <p class="input-info">Panjang maksimum teks: 10 karakter</p>
    <p v-if="isRedEmail" class="red-text">Email Kucing tidak valid!</p>
    <p>Nilai input email: <span :class="{ 'red-text': isRedEmail }">{{ email }}</span></p>
    <p>Password Kucing:</p>
    <!-- Input password -->
    <input type="password" v-model="password" :style="{ 'background-color': buttonBackgroundColor }" @blur="validatePassword">
    <p class="input-info">Panjang maksimum teks: 10 karakter</p>
    <p v-if="isRedPassword" class="red-text">Password Kucing harus memiliki setidaknya 6 karakter dan minimal satu angka!</p>
    <p>Nilai input password: <span :class="{ 'red-text': isRedPassword }">{{ password }}</span></p>
   
    <!-- Pilihan jenis kucing -->
    <p>Pilih Jenis Kucing:</p>
    <select v-model="jenisKucing">
      <option value="">Pilih Jenis Kucing</option>
      <option value="orange">Kucing Orange</option>
      <option value="hitam">Kucing Hitam</option>
    </select>
    
    <!-- Tombol untuk mengubah warna latar belakang -->
    <button :style="{ 'background-color': buttonBackgroundColor }" @click="changeColor">Ubah Warna Latar Belakang Tombol</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      isRedEmail: false,
      isRedPassword: false,
      buttonBackgroundColor: '#E6B3B3',
      jenisKucing: '', // Tambahkan data untuk jenis kucing
    }
  },
  methods: {
    validateEmail() {
      // Regular expression for email validation
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      this.isRedEmail = !emailRegex.test(this.email);
    },
    validatePassword() {
      // Password validation logic (example: minimum length of 6 characters and at least one number)
      this.isRedPassword = this.password.length < 6 || !/\d/.test(this.password);
    },
    changeColor() {
      this.buttonBackgroundColor = 'blue';
    },
  }
}
</script>

<style>
/* CSS Styles */
.NAJWA {
  background-image: url('./src/assets/orange2.jpg');
  background-size: cover; /* Agar gambar mengisi seluruh area background */
  background-position: center; /* Posisikan gambar di tengah */
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1 {
  color: #333;
  height: 10%;
}

p {
  color: #555;
  margin-bottom: 5px;
  text-align: left;
}

input[type="text"],
input[type="password"],
select {
  width: 20%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
  box-sizing: border-box;
  z-index: 2;
}

.input-info {
  font-size: 14px;
  color: #999;
  margin-top: -10px;
  margin-bottom: 10px;
}

span {
  font-size: 18px;
  color: #333;
  font-weight: bold;
}

.red-text {
  color: red;
}

button {
  padding: 5px 5px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 2px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #2980b9;
}

/* Style untuk album gambar */
.album {
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
}

.album img {
  width: 100px;
  height: auto;
  margin: 5px;
}
</style>
