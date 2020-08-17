<template>
  <div>
    <InquiryContent />
    <Footer />
  </div>
</template>

<script>
import Footer from '../components/Footer.vue'
import InquiryContent from '../components/InquiryContent.vue';

export default {
  name: "Inquiry",
  components: {
    Footer,
    InquiryContent,
  },
}
</script>

