<template>
    <nav id="navigation">
        <a href="/"><h1>Quadstone Global</h1></a>
        <ul >
            <a href="/" class="nav-link">Home</a>
        </ul>
    </nav>
</template>

<script>
export default {
    name: 'NavbarInquiryPage'
}
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


@media (max-width: 620px) {

    a {
        display: flex;
        align-items: center;
    }

    h1 {
        font-size: 20px;
    }

    nav {
       padding: 11px 17px;

       a.nav-link {
           padding-right: 0px;
       }
    }
}
</style>