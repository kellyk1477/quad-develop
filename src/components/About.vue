<template>
    <div>
        <div class="about-container">
            <div class="about-content">
                <h1>About Us</h1>
                <p>
                    JJSC Global Inc. d/b/a Quadstone Global is an international consulting firm founded by Justin Constantatos, Caesar Ho, Judy Ku and Susan Shin,
                    whose collective experiences serve clients all over world in various aspects related to Personal Protective Equipment (“PPE”). Although Quadstone 
                    Global advises on comprehensive PPE sourcing, procurement and acquisitions, it specializes in protective gloves for industrial and medical use.
                    Quadstone focuses on the following main aspects as it pertains to gloves: 1) sourcing and procurement of existing inventory/OTG; 2) sustainable
                    production contracts; and 3) proprietary, direct product sales OTG.
                </p>
                <button><a href="./jjsc-guideline-final.pdf" target="_blank">Financing | Prices</a></button>
            </div>
            <div class="about-image"></div>
        </div>
        <div class="about-container-two">
            <div class="about-content">
                <h1>About Us</h1>
                <p>
                    JJSC Global Inc. d/b/a Quadstone Global is an international consulting firm founded by Justin Constantatos, Caesar Ho, Judy Ku and Susan Shin,
                    whose collective experiences serve clients all over world in various aspects related to Personal Protective Equipment (“PPE”). Although Quadstone 
                    Global advises on comprehensive PPE sourcing, procurement and acquisitions, it specializes in protective gloves for industrial and medical use.
                    Quadstone focuses on the following main aspects as it pertains to gloves: 1) sourcing and procurement of existing inventory/OTG; 2) sustainable
                    production contracts; and 3) proprietary, direct product sales OTG.
                </p>
                <button>Financing | Prices</button>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: "About",
}
</script>

<style lang="scss" scoped>

h1 {
    font-size: 48px;
    margin-bottom: 54px;
}

button {
    font-size: 13px;
    letter-spacing: 2px;
    width: fit-content;
    margin-top: 20px;
    padding: 11px 36px;
    border: 1px solid #caccce;
    text-transform: uppercase;
    transition: all 0.2s;

    &:hover {
        background: rgb(202, 200, 200);
    }
}

.about-container-two {
    width: 100%;
    height: 80vh;
    // background: red;
    display: flex;
    font-family: "Assistant";

    h1 {
        font-size: 40px;
        margin-bottom: 57px;
    }

    button {
        font-family: "Assistant";
        background: black;
        color: white;
        margin-top: 26px;
    }

    .about-content {
        font-family: "Antic Didone";
        max-width: 780px;
        margin: auto;
        // background: green;

        p {
            font-size: 17px;
            line-height: 30px;
            font-family: "Assistant";
        }
    }
}

.about-container {
    width: 100%;
    height: 100vh;
    // background: red;
    display: flex;
    flex-direction: row;
    padding: 100px 170px;
    font-family: "Antic Didone";
    font-family: "Assistant";

    div {
        flex: 1;
        // background: blue;
        height: 100%; 
        margin: auto;
    } 

    .about-content {
        flex: 1;
        margin-right: 20px;
        padding: 0px 180px 0px 160px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        // border: 1px solid black;

        p {
            font-size: 16px;
            line-height: 26px;
            font-family: "Assistant";
        }
    }  

    .about-image {
        border: 1px solid black;
    }
}

</style>