<template>
    <v-app-bar 
        app
        prominent
        shrink-on-scroll
        src="https://picsum.photos/1920/1080?random"
        fade-img-on-scroll>
        <ul>
            <li>
                <a href="#about">About Us</a>
            </li>
            <li>
                <a href="#footer">Contact</a>
            </li>
            <li>
                <a href="/inquiry">Inquiry</a>
            </li>
        </ul>
    </v-app-bar>
</template>

<script>
// refer to app prop for v-app-bar component (vuetify)
export default {
    name: "Navbar",
}
</script>

<style lang="scss" scoped>
    ul {
        display: flex;
    }
    //   <v-app-bar-nav-icon></v-app-bar-nav-icon>
    //   <v-toolbar-title>Title</v-toolbar-title>
    //   <v-spacer></v-spacer>
    //   <v-btn icon>
    //     <v-icon>mdi-magnify</v-icon>
    //   </v-btn>
    //   <v-btn icon>
    //     <v-icon>mdi-heart</v-icon>
    //   </v-btn>
    //   <v-btn icon>
    //     <v-icon>mdi-dots-vertical</v-icon>
    //   </v-btn>
</style>