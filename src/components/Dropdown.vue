<template>
  <div class="dropdown-container">
        <div :class="{ 'dropdown-backdrop': isOpen }" @click="openMenu">
            <div class="menu-icon-wrap"  @click="openMenu" >
                <img src="../assets/images/menuIcon.png" alt="Menu" class="menu-icon">
            </div>
        </div>
        <transition name="dropdown" appear>
            <div class="sub-menu" v-if="isOpen">
                <div class="links">
                    <a href="/">Home</a>
                    <a href="#about" @click="openMenu">About Us</a>
                    <a href="#contact" @click="openMenu">Contact Us</a>
                    <a href="/inquiry" class="inquiry-link">Inquiries</a>
                </div>
            </div>
        </transition>
  </div>
</template>

<script>
import $ from 'jquery'
import MenuIcon from '../assets/images/working.png'

export default {
    name: 'Dropdown',
    data: () => ({
        isOpen: false,
        menuIcon: MenuIcon
    }),
    methods: {
        openMenu(e) {
            e.stopPropagation()
            this.isOpen = !this.isOpen
        }
    }

}
</script>

<style lang="scss" scoped>

.dropdown-container {
  display: flex;
  align-items: center;
}

.menu-icon-wrap, .menu-icon {
    width: 30px;
    height: 30px;
    cursor: pointer;
}

.sub-menu {
  position: fixed;
//   background: rgba(0, 0, 0, 0.726);
  background: rgba(223, 222, 222, 0.78);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.1);

  box-sizing: border-box;
  width: 100%;
  left: 0px;
  bottom: 0px;

  border-radius: 20px 20px 0px 0px;
  padding: 3px 0px 20px 0px;

  .links {
    display: flex;
    flex-direction: column;
    padding: 10px 20px 0px 20px;

    a {
      padding: 15px 0px;
      padding-bottom: 17px;
      font-weight: 400;
      font-size: 15px;
      line-height: 21px;
      color: #474646;
      border-bottom: 1px solid rgba(202, 201, 201, 0.37);

      &:hover {
          font-weight: 500;
          color: #363535;
      }

      &:focus {
          font-weight: 500;
          color: #4d4c4c;
      }
    }

    .inquiry-link {
        font-weight: bold;
        border-bottom: none;

        &:hover {
            font-weight: bold;
            color: black;
        }

        &:focus {
            font-weight: bold;
            color: black;
        }
    }
  }
}

.dropdown-enter-active,
.dropdown-leave-active {
  transition: all 0.25s ease-out;
}

.dropdown-enter,
.dropdown-leave-to {
  // opacity: 0;
  transform: translateY(100vh);
}

.dropdown-backdrop:before {
  content: '';
  position: fixed;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100vh;
  background: rgba(31, 30, 30, 0.247);

  animation-name: fade-in;
  animation-duration: 0.25s;
  opacity: 1;
}
</style>
