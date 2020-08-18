<template>
    <div class="landing-with-nav">
      <nav id="navigation">
        <h1>Quadstone Global</h1>
         <ul>
           <li>Home</li>
           <li>About</li>
           <li>Contact Us</li>
           <li>
              <a href="/inquiry">Inquiries</a>
            </li>
         </ul>
      </nav>
    </div>
</template>

<script>
export default {
  name: 'Navbar',
  mounted() {
    this.addScrollListener()
  },
  methods: {
    addScrollListener() {
      let nav = document.getElementById('navigation')
      window.onscroll = function() {
        if (window.pageYOffset > 100) {
          nav.style.background = "white";
          nav.style.borderBottom = "1px solid #E6E6E6"
          nav.style.color = "black"
        } else {
          nav.style.color = "white"
          nav.style.background = "transparent";
          nav.style.borderBottomStyle = "none"
        }
      }
    }
  },
};
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Maitree:wght@200;300&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Antic+Didone&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Assistant:wght@200;300;400&display=swap');

h1 {
  font-family: 'Antic Didone';
  font-size: 23px;
  font-weight: 300;
  color: black;
}

.landing-with-nav {
  width: 100%;
  height: 100vh;
  background-image: url('../assets/images/main-landscape.jpg');
  background-size: cover;
  background-repeat: no-repeat;

  nav {
    width: 100%;
    padding: 11px 47px;
    position: fixed;
    top: 0px;
    text-align: center;
    transition: 0.5s;

    display: flex;
    justify-content: space-between;
    color: white;

    li {
      cursor: pointer;
      font-size: 13px;
      font-family: "Assistant";
      font-weight: 400;
      letter-spacing: 1.2px;
      list-style-type: none;
      text-transform: uppercase;
      display: inline-block;
      padding: 8px 29px;
      border-radius: 10px;
      transition: 1.5s;

      &:hover {
        background: rgb(63, 63, 63);
      }

      a {
        color: inherit;
      }
    }
  }
}
</style>


