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
  <div class="desktop-nav">
    <div class="nav-one">
      <img src="./assets/images/logo.svg" alt="logo">
      <nav>
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
      </nav>
    </div>
    <div class="nav-two">
      <nav>
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
      </nav>
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
      <input type="text" v-model="oldLink" placeholder="Shorten a link here..." required>
      <button @click="shortLink" class="short-btn">
        <p v-if="!gettingLink">Shorten It!</p>
        <img src="./assets/images/load.svg" alt="load" v-else>
      </button>
    </div>
    <div class="shorted">
      <p class="origin-url">
        {{ oldLink }}
      </p>
      <p class="short-url">
        {{ newLink }}
      </p>
      <button @click="copyLink" class="short-btn" v-if="!linkCopy">
        Copy
      </button>
      <button class="copy-btn" v-else>
        Copied!
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
      <div class="feature one">
        <img src="./assets/images/icon-detailed-records.svg" alt="detailed-records">
        <h2>Detailed Records</h2>
        <p>Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions.</p>
      </div>
      <div class="stroke"></div>
      <div class="feature two">
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
import axios from 'axios'
import useClipboard from 'vue-clipboard3'

export default {
  setup() {
    const modal = ref(false)
    const oldLink = ref('')
    const linkData = ref('')
    const newLink = ref('')
    const gettingLink = ref(false)
    const linkCopy = ref(false)

    const { toClipboard } = useClipboard()

    const modalOption = () => {
      if(modal.value == false) {
        modal.value = true
        console.log('shown')
      } else {
        modal.value = false
        console.log('hidden')
      }
    }

    const shortLink = async () => {
      gettingLink.value = true
      const api_url = 'https://api.shrtco.de/v2/shorten?url='
      const givenLink = oldLink.value
      const url = api_url + givenLink
      axios.post(url)
      .then(response => {
        gettingLink.value = false
        linkData.value = response.data
        newLink.value = linkData.value.result.short_link
        console.log(newLink)
        document.querySelector('.shorted').style.display = 'block'
      })
      .catch(error => {
        console.log(error)
      })
    }

    const copyLink = async () => {
      try {
        await toClipboard(newLink.value)
        console.log('Copied to clipboard')
        linkCopy.value = true
        oldLink.value = ''
      } catch (e) {
        console.error(e)
      }
    }

    return {
      oldLink,
      shortLink,
      gettingLink,
      newLink,
      modal,
      modalOption,
      copyLink,
      linkCopy
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

.desktop-nav {
  display: none;
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

.main .shorted {
  margin-top: 70px;
  width: 100%;
  padding: 20px;
  border-radius: 10px;
  background-color: hsl(0, 0%, 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  display: none;
}

.main .shorted .origin-url {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  border-bottom: 1px solid grey;
}

.main .shorted .short-url {
  width: 100%;
  padding: 10px;
  color: hsl(180, 66%, 49%);
}

.main .shorted .short-btn {
  width: 100%;
  color: #fff;
  background-color: hsl(180, 66%, 49%);
  padding: 15px;
  border: none;
  border-radius: 10px;
  font-weight: 700;
}

.short-btn img {
  width: 24px;
}

.main .shorted .copy-btn {
  width: 100%;
  color: #fff;
  background-color: hsl(255, 11%, 22%);
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
  text-align: center;
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

@media(min-width: 900px) {
  .header-box {
    display: none;
  }

  .desktop-nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 40px;
  }

  .nav-one {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .nav-one img {
    margin-right: 10px;
  }

  .nav-one nav {
    list-style: none;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .nav-one nav li {
    padding: 0 15px;
  }

  .nav-one nav li a  {
    text-decoration: none;
    color: hsl(257, 7%, 63%);
    font-weight: 700;
  }

  .nav-two nav {
    list-style: none;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .nav-two nav li {
    padding: 0 15px;
  }

  .nav-two nav li a {
    text-decoration: none;
    color: hsl(257, 7%, 63%);
    font-weight: 700;
  }

  .nav-two nav .sign {
    background-color: hsl(180, 66%, 49%);
    padding: 10px 20px;
    border: none;
    border-radius: 50px;
    font-weight: 700;
  }

  .nav-two nav .sign a {
    color: #fff;
  }

  .hero-section {
    flex-direction: row-reverse;
    justify-content: space-between;
  }

  .hero-image {
    width: 50%;
  }

  .hero-image img {
    width: 500px;
  }

  .hero-text {
    margin-top: 0px;
    text-align: left;
    margin-left: 80px;
    margin-right: 60px;
  }

  .main .short-it {
    top: -50px;
    padding: 30px;
    background-image: url('./assets/images/bg-shorten-desktop.svg');
    background-position: 100px;
    flex-direction: row;
  }

  .main .short-it input {
    padding: 10px;
    margin-bottom: 0px;
  }

  .main .short-it .short-btn {
    width: 20%;
    color: #fff;
    background-color: hsl(180, 66%, 49%);
    padding: 10px;
    margin-left: 20px;
    border: none;
    border-radius: 10px;
    font-weight: 700;
  }

  .main .shorted {
    width: 80%;
    padding: 20px;
    flex-direction: row;
    margin-top: 30px;
    margin-left: 10%;
  }
  
  .main .shorted .origin-url {
    width: 80%;
    padding: 8px;
    border-bottom: none;
    margin-bottom: 0;
  }

  .main .shorted .short-url {
    width: 40%;
    padding: 8px;
    color: hsl(180, 66%, 49%);
    text-align: right;
    margin-right: 10px;
  }

  .main .shorted .short-btn {
    width: 20%;
    color: #fff;
    background-color: hsl(180, 66%, 49%);
    padding: 10px;
    border: none;
    border-radius: 10px;
    font-weight: 700;
  }

  .main .shorted .copy-btn {
    display: none;
    width: 20%;
    color: #fff;
    background-color: hsl(255, 11%, 22%);
    padding: 10px;
    border: none;
    border-radius: 10px;
    font-weight: 700;
  }

  .about {
    margin-bottom: 50px;
  }
  
  .features {
    flex-direction: row;
    margin-top: 20px;
    padding-top: 20px;
  }


  .one {
    margin-top: 70px;
  }

  .two {
    margin-top: 170px;
  }

  .stroke {
    width: 200px;
    height: 3px;
  }

  .footer {
    padding: 50px 40px;
    flex-direction: row;
    align-items: baseline;
    justify-content: space-between;
  }

  .footer .footer-feature h3 {
    margin-bottom: 0px;
  }

  .resources {
    margin: 0;
  }
}
</style>
