<template>
  <div>
    <div class="landing-with-nav">
      <nav id="navigation">
         <ul>
           <li>Home</li>
           <li>About</li>
           <li>Contact Us</li>
           <li>Inquiries</li>
         </ul>
      </nav>
    </div>
    <div class="section-one"></div>
    <div class="section-one"></div>
  </div>
</template>

<script>
export default {
  name: 'LandingPage',
  mounted() {
    this.addScrollListener()
  },
  methods: {
    addScrollListener() {
      let nav = document.getElementById('navigation')
      window.onscroll = function() {
        if (window.pageYOffset > 100) {
          nav.style.background = "grey";
        } else {
          nav.style.background = "transparent";
        }
      }
    }
  },
  data: () => ({
    //
  }),
};
</script>

<style lang="scss" scoped>

.landing-with-nav {
  width: 100%;
  height: 100vh;
  background: black;

  nav {
    width: 100%;
    padding: 20px;
    position: fixed;
    top: 0px; 
    transition: 0.5s;
    text-align: center;

    li {
      list-style-type: none;
      display: inline-block;
      padding: 10px 50px;
      color: white; 
      font-size: 20px;
      cursor: pointer;
      border-radius: 10px;
      transition: 0.5s;

      &:hover {
        background: rgb(63, 63, 63);
      }
    }
  }
}

.section-one {
  width: 100%;
  height: 100vh;
  background: rgb(9, 41, 9);
  margin: 20px auto;
}

  section {
    height: 100vh;
    background-image: url('../assets/aesop-pic.jpg');
    border-bottom: 2px solid black;
  }
</style>
