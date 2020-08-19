<template>
    <nav id="navigation">
        <h1><a href="/">Quadstone Global</a></h1>
        <div v-if="showMenuIcon"><li><a href="/inquiry">Inquiries</a></li></div>
        <ul v-else>
           <li><a href="/">Home</a></li>
           <li>About</li>
           <li>Contact Us</li>
           <li><a href="/inquiry">Inquiries</a></li>
        </ul>
    </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data: () => ({
      showMenuIcon: false
  }),
  mounted() {
    // this.addScrollListener()
    this.onWindowResize()
    window.addEventListener("resize", this.onWindowResize);
  },
  destroyed() {
    window.removeEventListener("resize", this.onWindowResize);
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
    },
    onWindowResize() {
        if (window.innerWidth < 820) {
            this.showMenuIcon = true
        } else {
            this.showMenuIcon = false
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
    white-space: nowrap;

    a {
        color: inherit;
    }
}

  nav {
    width: 100%;
    padding: 11px 47px;
    position: fixed;
    top: 0px;
    text-align: center;
    transition: 0.5s;

    background: white;
    display: flex;
    justify-content: space-between;
    color: black;
    border-bottom: 1px solid rgb(228, 222, 222);

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
      border-radius: 8px;
      transition: 1.3s;

      &:hover {
        background: rgba(163, 162, 162, 0.459);
      }

      a {
        color: inherit;
      }
    }
}
</style>


