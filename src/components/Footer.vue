<template>
  <section id="contact">
    <div class="contact-info">
        <div class="contact-details">
            <h1>Contact</h1>
            <div v-for="(person, viz) in info" :key="viz">
                <h3>{{ person.name }}</h3>
                <a :href="'mailto:' + person.email">{{ person.email }}</a>
                <p>{{ person.tel }}</p>
            </div>
            <h3>General Inquiry</h3>
            <a href="mailto:info@quadstoneglobal.com">info@quadstoneglobal.com</a>
        </div>
        <div class="company-name">
            <p>Quadstone Global</p>
            <p>JJSC Gloabl Inc.</p>
        </div>
    </div>
    <div class="contact-address">
      <h1>Address</h1>
      <p>TrueCare, LLC <br /> 53-594 Kamehameha Hwy <br /> Hauula, HI 96717</p>
    </div>
  </section>
</template>

<script>
const INFO = {
    justin: {
        name: 'Justin Constantatos',
        email: 'justinc@quadstoneglobal.com',
        tel: '631) 922 - 1653'
    },
    judy: {
        name: 'Judy S. Ku',
        email: 'judyku@quadstoneglobal.com',
        tel: '347) 615 - 0430'
    },
}

export default {
    name: "Footer",
    data: () => ({
        info: INFO
    })
}
</script>

<style lang="scss" scoped>

#contact {
    width: 100%;
    height: 600px;
    background: #212121;
    background: black;
    font-family: "Assistant";
    font-size: 15px;
    color: white;
    display: flex;
    padding: 60px 270px 40px 270px;
}

.contact-info {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-right: 80px;

    
    .company-name p {
        color: white !important;
    }
}

.contact-address p {
    color: white !important;
    line-height: 30px;
}

h1 {
    text-transform: uppercase;
    font-size: 17px;
    font-weight: 600;
    letter-spacing: 1px;
    margin-bottom: 35px;
}

h3 {
    font-size: 16px;
    font-weight: 600;
    letter-spacing: 0.6px;
    margin-top: 10px;
    margin-bottom: 10px;
}

p {
    margin: 0 !important;
    color: rgb(194, 190, 190) !important;
    line-height: 22px;
    letter-spacing: 0.5px !important;
}

a {
    color: white !important;
    text-decoration: none;
    transition: all 0.3s;
    letter-spacing: 0.2px !important;

    &:hover {
        color: rgb(182, 179, 179) !important;
    }
}

    .contact-details  {
       
       div:first-child {
           background: red;
       }
    }

</style>