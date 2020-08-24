<template>
  <div>
    <NavbarInquiryPage />
    <InquiryContent />
    <Footer />
  </div>
</template>

<script>
import Footer from '../components/Footer.vue'
import InquiryContent from '../components/InquiryContent.vue';
import NavbarInquiryPage from '../components/NavbarInquiryPage.vue'


export default {
  name: "Inquiry",
  components: {
    NavbarInquiryPage,
    Footer,
    InquiryContent,
  },
}
</script>

