<template>
  <div class="container">
    <div class="generator-container">
      <h2>Website QR Code Generator</h2>
      <div class="generator">
        <form method="post" autocomplete="off" ref="form" @submit.prevent="generateQR">
          <input
            class="site-input"
            type="text"
            v-model="site"
            name="site"
            placeholder="Enter a site name"
          />
          <br />
          <input class="submit-btn" type="submit" value="Generate" />
          <p class="error-msg">{{ errorMsg }}</p>
        </form>
        <img v-bind:class="{'qr-img': site == ''}" v-bind:src="imageUrl" alt />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "QrGenerator",
  data() {
    return {
      site: "",
      imageUrl: "",
      errorMsg: "",
    };
  },
  methods: {
    generateQR() {
      if (this.site === "") {
        this.errorMsg = "Please enter a valid site name";
      } else {
        this.errorMsg = "";
        // Checks if site includes "www." if not add it to the beginning
        if (!this.site.includes("www.")) {
          this.site = "www." + this.site;
          this.imageUrl =
            "https://qrtag.net/api/qr_12.png?url=https://" + this.site;
          console.log(this.site);
        } else {
          this.imageUrl =
            "https://qrtag.net/api/qr_12.png?url=https://" + this.site;
        }
        // Checks if site includes "." after the www. if not add it to the end
        if (!this.site.substr(6).includes(".")) {
          this.site = this.site + ".com";
          this.imageUrl =
            "https://qrtag.net/api/qr_12.png?url=https://" + this.site;
          console.log(this.site);
        } else {
          this.imageUrl =
            "https://qrtag.net/api/qr_12.png?url=https://" + this.site;
        }
        // Checks if site includes "www." & ".com" if not add it
        if (!this.site.includes("www.") && !this.site.includes(".com")) {
          this.site = "www." + this.site + ".com";
          this.imageUrl =
            "https://qrtag.net/api/qr_12.png?url=https://" + this.site;
        } else {
          this.imageUrl =
            "https://qrtag.net/api/qr_12.png?url=https://" + this.site;
        }
      }
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.generator-container {
  background-color: #fff;
  width: 50vw;
  border-radius: 10px;
}

.generator {
  display: flex;
  justify-content: center;
  padding: 30px;
}

form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-right: 50px;
}

.site-input {
  padding: 10px;
  width: 12vw;
  border-radius: 3px;
  border: 1.5px solid rgb(148, 148, 148);
}

.site-input:focus {
  outline: none;
}

.submit-btn {
  background: #be93c5; /* fallback for old browsers */
  border: none;
  color: #fff;
  padding: 10px 30px;
  border-radius: 10px;
  cursor: pointer;
  width: 12vw;
}

.submit-btn:hover {
  background: #7bc6cc;
  transition: 2s;
}

.submit-btn:focus {
  outline: none;
}

.qr-img {
  visibility: hidden;
}

img {
  width: 15vw;
  height: 15vw;
  margin-left: 50px;
}

.error-msg {
  color: red;
}
</style>