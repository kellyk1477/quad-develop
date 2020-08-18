<template>
  <div>
    <Navbar />
    <InquiryContent />
    <Footer />
  </div>
</template>

<script>
import Footer from '../components/Footer.vue'
import InquiryContent from '../components/InquiryContent.vue';
import Navbar from '../components/Navbar.vue'

export default {
  name: "Inquiry",
  components: {
    Navbar,
    Footer,
    InquiryContent,
  },
}
</script>

