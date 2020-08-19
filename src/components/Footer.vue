<template>
  <section id="contact">
      <div class="contact-container">
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
        </div>
        <div class="contact-address">
            <h1>Address</h1>
            <p>JJSC Global Inc.<br />Quadstone Global<br />318 N Carson St. STE 208<br />Carson City, NV 89701</p>
        </div>
      </div>
      <div class="company-name">
        <p>Quadstone Global</p>
        <p>JJSC Gloabl Inc.</p>
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
    padding: 60px 0px 60px 0px;
    display: flex;
    flex-direction: column;

    .contact-container {
        width: 70%;
        height: 85%;
        display: flex;
        margin: auto;
    }
}

.company-name {
    width: 70%;
    margin: auto;
    
    p {
        color: white !important;
        font-size: 14px;
        font-weight: 600;
        letter-spacing: 0.2px;
    }
}

.contact-info {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-right: 80px;
}

.contact-address p {
    color: white !important;
    line-height: 30px;
    min-width: 195px;
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
    min-width: 195px;
    
    div:first-child {
        background: red;
    }
}

@media (max-width: 740px) {

    .contact-info {
        margin-bottom: 20px;
        margin-right: 0px;
    }

    h1 {
        line-height: 38px;
        margin-bottom: 20px;
        border-bottom: 1px solid rgba(201, 201, 201, 0.452);
    }

    #contact {
        height: 670px;
        padding: 40px 0px 40px 0px;

        .contact-container {
            flex-direction: column;
            width: 90%;
        }

        .contact-address p {
            line-height: 26px;
        }

        .company-name {
            width: 90%;
            font-size: 13px;
            font-weight: 600;
            letter-spacing: 0.2px;

            p {
                font-size: 13px;
            }
        }
    }
    
}

</style>