<template>
    <nav id="navigation">
        <h1><a href="/">Quadstone Global</a></h1>

        <dropdown v-if="showMenuIcon" />
        <ul v-else >
            <a v-for="(item, viz) in navList" :key="viz" :href="item.link" class="nav-link" @click="scrollToSection" >{{ item.linkName }}</a>
        </ul>
    </nav>
</template>

<script>
import $ from 'jquery'
import Dropdown from './Dropdown.vue'
import MenuIcon from '../assets/images/menuIcon.png'

const NavItems = {
    home: {
        linkName: "Home",
        link: "#home"
    },
    about: {
        linkName: "About",
        link: "#about"
    },
    contact: {
        linkName: "Contact",
        link: "#contact"
    },
    inquiry: {
        linkName: "Inquiries",
        link: "/inquiry"
    },
}

const InquiryNavItem = {
    home: {
        linkName: "Home",
        link: "/"
    },
}

export default {
  name: 'Navbar',
  components: {
      Dropdown
  },
  data: () => ({
      showMenuIcon: false,
      menuIcon: MenuIcon,
      navItems: NavItems,
      inquiryNavItem: InquiryNavItem,
      navList: null
  }),
  mounted() {
    this.onWindowResize()
    window.addEventListener("resize", this.onWindowResize);

    if (window.location.href.includes("/inquiry")) {
        this.navList = this.inquiryNavItem
    } else {
        this.navList = this.navItems
    }
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
    scrollToSection(e) {
        const linkHash = e.target.hash

        if (linkHash !== '' && window.innerWidth < 1240) {
            e.preventDefault()
            $('html, body').animate(
                {
                    scrollTop: $(linkHash).offset().top - 50,
                },
                800,
            )
        } else if (linkHash !== '') {
            e.preventDefault()
            $('html, body').animate(
                {
                    scrollTop: $(linkHash).offset().top - 100,
                },
                800,
            )
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
    z-index: 1;

    background: white;
    display: flex;
    justify-content: space-between;
    color: black;
    border-bottom: 1px solid rgb(228, 222, 222);

    a.nav-link {
      cursor: pointer;
      font-size: 13px;
      font-family: "Assistant";
      font-weight: 400;
      letter-spacing: 1.2px;
      list-style-type: none;
      text-transform: uppercase;
      display: inline-block;
      padding: 8px 25px;
      border-radius: 8px;
      transition: 1.3s;
      color: inherit;

      &:hover {
        font-weight: 500;
        background: rgba(211, 209, 209, 0.452);
      }
    }
}

@media (max-width: 600px) {

    h1 {
        font-size: 20px;
    }

    nav {
        padding: 11px 17px;
        display: flex;
        align-items: center;
    }
}
</style>


