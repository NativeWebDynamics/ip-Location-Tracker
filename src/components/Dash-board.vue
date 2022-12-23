<template>
  <div>
    <b-navbar type="dark" variant="dark">
      <b-navbar-nav>
        <div>
          <b-nav-item href="#">Location finder</b-nav-item>
        </div>

        <!-- Navbar dropdowns -->
        <button class="button2">Sign up</button>
      </b-navbar-nav>
    </b-navbar>
    <div class="container-fluid mt-4">
      <div class="row">
        <div class="col-lg-6">
          <div>
            <button class="button2 mt-2" @click="getdata">
              Get Location

              <b-spinner v-show="!loading" class="spinner"></b-spinner>
            </button>
            <input
              class="input"
              v-model="ip"
              type="text"
              placeholder="Enter your IP"
            />
          </div>

          <div class="mt-3">
            <b-list-group>
              <b-list-group-item>Query: {{ query }}</b-list-group-item>
              <b-list-group-item>Status: {{ status }}</b-list-group-item>
              <b-list-group-item>Countary {{ country }}</b-list-group-item>
              <b-list-group-item>City: {{ city }}</b-list-group-item>
              <b-list-group-item>Latitude: {{ lat }}</b-list-group-item>
              <b-list-group-item>Longitude: {{ lon }}</b-list-group-item>
              <b-list-group-item>Timezone: {{ timezone }}</b-list-group-item>
              <b-list-group-item>Isp: {{ isp }}</b-list-group-item>
              <b-list-group-item>Organization: {{ org }}</b-list-group-item>
            </b-list-group>
          </div>
        </div>

        <div class="col-lg-6 mt-3">
          <p class="text-center button2">Your Location</p>
          <iframe
            width="730"
            height="350"
            frameborder="0"
            scrolling="no"
            marginheight="0"
            marginwidth="0"
            v-bind:src="this.src"
          ></iframe>
        </div>
      </div>
    </div>
    <footer class="footer-section mt-4">
      <div class="container">
        <div class="footer-cta pt-5 pb-5">
          <div class="row">
            <div class="col-xl-4 col-md-4 mb-30">
              <div class="single-cta">
                <i class="fas fa-map-marker-alt"></i>
                <div class="cta-text">
                  <h4>Find us</h4>
                  <span>1010 Avenue, sw 54321, chandigarh</span>
                </div>
              </div>
            </div>
            <div class="col-xl-4 col-md-4 mb-30">
              <div class="single-cta">
                <i class="fas fa-phone"></i>
                <div class="cta-text">
                  <h4>Call us</h4>
                  <span>9876543210 0</span>
                </div>
              </div>
            </div>
            <div class="col-xl-4 col-md-4 mb-30">
              <div class="single-cta">
                <i class="far fa-envelope-open"></i>
                <div class="cta-text">
                  <h4>Mail us</h4>
                  <span>mail@info.com</span>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="footer-content pt-5 pb-5">
          <div class="row">
            <div class="col-xl-4 col-lg-4 mb-50">
              <div class="footer-widget">
                <div class="footer-logo"></div>
                <div class="footer-text">
                  <p>
                    Lorem ipsum dolor sit amet, consec tetur adipisicing elit,
                    sed do eiusmod tempor incididuntut consec tetur adipisicing
                    elit,Lorem ipsum dolor sit amet.
                  </p>
                </div>
                <div class="footer-social-icon">
                  <span>Follow us</span>
                  <a href="#"><i class="fab fa-facebook-f facebook-bg"></i></a>
                  <a href="#"><i class="fab fa-twitter twitter-bg"></i></a>
                  <a href="#"><i class="fab fa-google-plus-g google-bg"></i></a>
                </div>
              </div>
            </div>
            <div class="col-xl-4 col-lg-4 col-md-6 mb-30">
              <div class="footer-widget">
                <div class="footer-widget-heading">
                  <h3>Useful Links</h3>
                </div>
                <ul>
                  <li><a href="#">Home</a></li>
                  <li><a href="#">about</a></li>
                  <li><a href="#">services</a></li>
                  <li><a href="#">portfolio</a></li>
                  <li><a href="#">Contact</a></li>
                  <li><a href="#">About us</a></li>
                  <li><a href="#">Our Services</a></li>
                  <li><a href="#">Expert Team</a></li>
                  <li><a href="#">Contact us</a></li>
                  <li><a href="#">Latest News</a></li>
                </ul>
              </div>
            </div>
            <div class="col-xl-4 col-lg-4 col-md-6 mb-50">
              <div class="footer-widget">
                <div class="footer-widget-heading">
                  <h3>Subscribe</h3>
                </div>
                <div class="footer-text mb-25">
                  <p>
                    Don’t miss to subscribe to our new feeds, kindly fill the
                    form below.
                  </p>
                </div>
                <div class="subscribe-form">
                  <form action="#">
                    <input type="text" placeholder="Email Address" />
                    <button><i class="fab fa-telegram-plane"></i></button>
                  </form>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="copyright-area">
        <div class="container">
          <div class="row">
            <div class="col-xl-6 col-lg-6 text-center text-lg-left">
              <div class="copyright-text">
                <p>
                  Copyright &copy; 2018, All Right Reserved
                  <a>Osama</a>
                </p>
              </div>
            </div>
            <div class="col-xl-6 col-lg-6 d-none d-lg-block text-right">
              <div class="footer-menu">
                <ul>
                  <li><a href="#">Home</a></li>
                  <li><a href="#">Terms</a></li>
                  <li><a href="#">Privacy</a></li>
                  <li><a href="#">Policy</a></li>
                  <li><a href="#">Contact</a></li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ip: "",
      query: "",
      status: "",
      country: "",
      loading: true,
      lat: "30.3753",
      lon: "69.3451",
      city: "London",
      timezone: "",
      org: "",
      isp: "",
      token: false,
      src: "",
    };
  },
  mounted() {
    this.src = `https://maps.google.com/maps?q=${this.lat}, ${this.lon}&z=15&output=embed`;
  },
  methods: {
    getdata() {
      if (this.ip == "") {
        alert("Feild cannot be Empty");
      }
      setTimeout(((this.loading = false), 3000));
      fetch(`http://ip-api.com/json/${this.ip}`)
        .then((response) => response.json())
        .then((data) => {
          console.log(data.lat);
          console.log(data.lon);
          this.query = data.query;
          this.status = data.status;
          this.country = data.country;
          this.countryCode = data.countryCode;
          this.region = data.region;
          this.timezone = data.timezone;
          this.isp = data.isp;
          this.org = data.org;
          this.city = data.city;
          this.lat = data.lat;
          this.lon = data.lon;
          this.src = `https://maps.google.com/maps?q=${this.lat}, ${this.lon}&z=15&output=embed`;
          setTimeout(((this.loading = true), 3000));
        });
    },
  },
};
</script>

<style scoped>
ul {
  margin: 0px;
  padding: 0px;
}
.input {
  height: 34px;
  margin-left: 10px;
}
.footer-section {
  background: #151414;
  position: relative;
}
.footer-cta {
  border-bottom: 1px solid #373636;
}
.single-cta i {
  color: #ff5e14;
  font-size: 30px;
  float: left;
  margin-top: 8px;
}
.cta-text {
  padding-left: 15px;
  display: inline-block;
}
.cta-text h4 {
  color: #fff;
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 2px;
}
.cta-text span {
  color: #757575;
  font-size: 15px;
}
.footer-content {
  position: relative;
  z-index: 2;
}
.footer-pattern img {
  position: absolute;
  top: 0;
  left: 0;
  height: 330px;
  background-size: cover;
  background-position: 100% 100%;
}
.footer-logo {
  margin-bottom: 30px;
}
.footer-logo img {
  max-width: 200px;
}
.footer-text p {
  margin-bottom: 14px;
  font-size: 14px;
  color: #7e7e7e;
  line-height: 28px;
}
.footer-social-icon span {
  color: #fff;
  display: block;
  font-size: 20px;
  font-weight: 700;
  font-family: "Poppins", sans-serif;
  margin-bottom: 20px;
}
.footer-social-icon a {
  color: #fff;
  font-size: 16px;
  margin-right: 15px;
}
.footer-social-icon i {
  height: 40px;
  width: 40px;
  text-align: center;
  line-height: 38px;
  border-radius: 50%;
}
.facebook-bg {
  background: #3b5998;
}
.twitter-bg {
  background: #55acee;
}
.google-bg {
  background: #dd4b39;
}
.footer-widget-heading h3 {
  color: #fff;
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 40px;
  position: relative;
}
.footer-widget-heading h3::before {
  content: "";
  position: absolute;
  left: 0;
  bottom: -15px;
  height: 2px;
  width: 50px;
  background: #ff5e14;
}
.footer-widget ul li {
  display: inline-block;
  float: left;
  width: 50%;
  margin-bottom: 12px;
}
.footer-widget ul li a:hover {
  color: #ff5e14;
}
.footer-widget ul li a {
  color: #878787;
  text-transform: capitalize;
}
.subscribe-form {
  position: relative;
  overflow: hidden;
}
.subscribe-form input {
  width: 100%;
  padding: 14px 28px;
  background: #2e2e2e;
  border: 1px solid #2e2e2e;
  color: #fff;
}
.subscribe-form button {
  position: absolute;
  right: 0;
  background: #ff5e14;
  padding: 13px 20px;
  border: 1px solid #ff5e14;
  top: 0;
}
.subscribe-form button i {
  color: #fff;
  font-size: 22px;
  transform: rotate(-6deg);
}
.copyright-area {
  background: #202020;
  padding: 25px 0;
}
.copyright-text p {
  margin: 0;
  font-size: 14px;
  color: #878787;
}
.copyright-text p a {
  color: #ff5e14;
}
.footer-menu li {
  display: inline-block;
  margin-left: 20px;
}
.footer-menu li:hover a {
  color: #ff5e14;
}
.footer-menu li a {
  font-size: 14px;
  color: #878787;
}
.button2 {
  margin-right: 10px;
  background-color: blueviolet; /* Green */
  border: none;
  color: white;
  margin-left: 10px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  padding-top: 5px;
  padding-bottom: 5px;
  padding-left: 10px;
  padding-right: 10px;
}

.spinner {
  height: 20px;
  width: 20px;
}
</style>
