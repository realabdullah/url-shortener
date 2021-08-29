<template>
  <div class="header-box">
    <div class="header">
      <img src="./assets/images/logo.svg" alt="logo">
      <div @click="modalOption" class="hamburger">
        <div></div>
        <div></div>
        <div></div>
      </div>
    </div>
    <div class="modal" v-if="modal">
      <ul class="modal-content">
        <li>
          <a href="#">
            Features
          </a>
        </li>
        <li>
          <a href="#">
            Pricing
          </a>
        </li>
        <li>
          <a href="#">
            Resources
          </a>
        </li>

  <hr>

        <li>
          <a href="#">
            Login
          </a>
        </li>
        <li class="sign">
          <a href="#">
            Sign Up
          </a>
        </li>
      </ul>
    </div>
  </div>
  <div class="hero-section">
    <div class="hero-image">
      <img src="./assets/images/illustration-working.svg" alt="illustration">
    </div>
    <div class="hero-text">
      <h1>More than just shorter links</h1>
      <p>Build your brand's recognition and get detailed insights on how your links are performing.</p>
      <button class="cta-btn">
        Get Started
      </button>
    </div>
  </div>
  <div class="main">
    <div class="short-it">
      <input type="text" placeholder="Shorten a link here...">
      <button class="short-btn">
        Shorten It!
      </button>
    </div>
    <div class="about">
      <h1>Advanced Statistics</h1>
      <p>Track how your links are performing across the web with our advanced statistics dashboard.</p>
    </div>
    <div class="features">
      <div class="feature">
        <img src="./assets/images/icon-brand-recognition.svg" alt="brand-recognition">
        <h2>Brand Recognition</h2>
        <p>Boost your brand recognition with each click. Generic links don't mean a thing. Branded links help instil confidence in your content.</p>
      </div>
      <div class="stroke"></div>
      <div class="feature">
        <img src="./assets/images/icon-detailed-records.svg" alt="detailed-records">
        <h2>Detailed Records</h2>
        <p>Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions.</p>
      </div>
      <div class="stroke"></div>
      <div class="feature">
        <img src="./assets/images/icon-fully-customizable.svg" alt="fully-customizable">
        <h2>Fully Customizable</h2>
        <p>Improve brand awareness and content discoverability through customizable links, supercharging audience engagement.</p>
      </div>
    </div>
  </div>
  <div class="cta-section">
    <h1>Boost your links today</h1>
    <button class="cta-btn">
      Get Started
    </button>
  </div>
  <div class="footer">
    <img src="./assets/images/footerlogo.svg" alt="logo">
    <ul class="footer-feature">
      <h3>Features</h3>
      <li>
        <a href="#">
          Link Shortening
        </a>
      </li>
      <li>
        <a href="#">
          Branded Links
        </a>
      </li>
      <li>
        <a href="#">
          Analytics
        </a>
      </li>
    </ul>
    <ul class="resources">
      <h3>Resources</h3>
      <li>
        <a href="#">
          Blog
        </a>
      </li>
      <li>
        <a href="#">
          Developers
        </a>
      </li>
      <li>
        <a href="#">Support</a>
      </li>
    </ul>
    <ul class="company">
      <h3>Company</h3>
      <li>
        <a href="#">
          About
        </a>
      </li>
      <li>
        <a href="#">
          Our Team
        </a>
      </li>
      <li>
        <a href="#">
          Careers
        </a>
      </li>
      <li>
        <a href="# ">
          Contact
        </a>
      </li>
    </ul>
    <ul class="socials">
      <li>
        <a href="#">
          <img src="./assets/images/icon-facebook.svg" alt="facebook">
        </a>
      </li>
      <li>
        <a href="#">
          <img src="./assets/images/icon-twitter.svg " alt="twitter">
        </a>
      </li>
      <li>
        <a href="#">
          <img src="./assets/images/icon-pinterest.svg" alt="pinterest">
        </a>
      </li>
      <li>
        <a href="#">
          <img src="./assets/images/icon-instagram.svg" alt="instagram">
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const modal = ref(false)

    const modalOption = () => {
      if(modal.value == false) {
        modal.value = true
        console.log('shown')
      } else {
        modal.value = false
        console.log('hidden')
      }
      
    }
    
    return {
      modal,
      modalOption
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@500;700&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}

.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 40px;
}

.hamburger div {
  width: 30px;
  height: 3px;
  background-color: hsl(0, 0%, 75%);
  margin: 5px;
}

.modal {
  margin: 4px 45px;
  padding: 40px;
  background-color: hsl(257, 27%, 26%);
  border-radius: 10px;
}

.modal-content {
  list-style: none;
  text-align: center;
}

.modal-content li {
  padding: 10px 0;
}

.modal-content li a  {
  text-decoration: none;
  color: #fff;
  font-weight: 700;
}

.modal-content .sign {
  color: #fff;
  background-color: hsl(180, 66%, 49%);
  padding: 15px 30px;
  border: none;
  border-radius: 50px;
  margin-top: 10px;
  font-weight: 700;
}

hr {
  margin: 10px 0;
}

.hero-section {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  padding: 40px;
}

.hero-image {
  width: 100%;
}

.hero-image img {
  width: 100%;
}

.hero-text {
  margin-top: 30px;
  text-align: center;
}

.hero-text h1 {
  color: hsl(257, 27%, 26%);
}

.hero-text p {
  margin-top: 20px;
  color: hsl(0, 0%, 75%);
}

.hero-text button {
  color: #fff;
  background-color: hsl(180, 66%, 49%);
  padding: 15px 30px;
  border: none;
  border-radius: 50px;
  margin-top: 20px;
  font-weight: 700;
}

.main {
  position: relative;
  background-color: hsl(0, 0%, 75%);
  margin-top: 100px;
  padding: 40px;
}

.main .short-it {
  position: absolute;
  top: -80px;
  left: 10%;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
  background-color: hsl(255, 11%, 22%);
  background-image: url('./assets/images/bg-shorten-mobile.svg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 100px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.main .short-it input {
  width: 100%;
  padding: 15px;
  border: none;
  border-radius: 10px;
  outline: none;
  margin-bottom: 10px;
}

.main .short-it input::placeholder {
  font-weight: bold;
  color: hsl(255, 11%, 22%);
}

.main .short-it .short-btn {
  width: 100%;
  color: #fff;
  background-color: hsl(180, 66%, 49%);
  padding: 15px;
  border: none;
  border-radius: 10px;
  font-weight: 700;
}

.about {
  text-align: center;
  margin: 100px 0;
}

.about h1 {
  color: hsl(260, 8%, 14%);
  margin-bottom: 20px;
}

.about p {
  color: hsl(257, 7%, 63%);
}

.features {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.feature {
  position: relative;
  padding: 30px;
  background-color: #fff;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
}

.feature img {
  position: absolute;
  top: -40px;
  width: 80px;
  padding: 20px;
  background-color: hsl(255, 11%, 22%);
  border-radius: 100px;
}

.feature h2 {
  margin-top: 45px;
  color: hsl(260, 8%, 14%);
}

.feature p {
  margin: 15px 0;
  line-height: 1.5em;
  color: hsl(257, 7%, 63%);
}

.stroke {
  width: 8px;
  height: 100px;
  background-color: hsl(180, 66%, 49%);
}

.cta-section {
  padding: 100px 20px;
  background-color: hsl(255, 11%, 22%);
  background-image: url('./assets/images/bg-shorten-mobile.svg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.cta-section h1 {
  color: #fff;
}

.cta-section .cta-btn {
  color: #fff;
  background-color: hsl(180, 66%, 49%);
  padding: 15px 30px;
  border: none;
  border-radius: 50px;
  margin-top: 20px;
  font-weight: 700;
}

.footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: hsl(260, 8%, 14%);
  padding: 50px 0;
}

.footer .footer-feature {
  text-align: center;
  list-style: none;
  margin: 30px 0;
}

.footer .footer-feature h3 {
  color: #fff;
  margin-bottom: 20px;
}

.footer .footer-feature li {
  padding: 10px 0;
}

.footer .footer-feature li a {
  text-decoration: none;
  color: hsl(257, 7%, 63%);
}

.resources {
  text-align: center;
  list-style: none;
  margin: 30px 0;
}

.resources h3 {
  color: #fff;
  margin-bottom: 20px;
}

.resources li {
  padding: 10px 0;
}

.resources li a {
  text-decoration: none;
  color: hsl(257, 7%, 63%);
}

.company {
  text-align: center;
  list-style: none;
  margin: 30px 0;
}

.company h3 {
  color: #fff;
  margin-bottom: 20px;
}

.company li {
  padding: 10px 0;
}

.company li a {
  text-decoration: none;
  color: hsl(257, 7%, 63%);
}

.socials {
  display: flex;
  align-items: center;
  justify-content: center;
  list-style: none;
}

.socials li {
  padding: 10px;
}
</style>
