<template>
  <div>
    <LogIn />
    <InscripForm />
     <Footer />
  </div>
</template>

<script>
import LogIn from './components/LogIn.vue';
import InscripForm from './components/InscripForm.vue';
import Footer from './components/Footer.vue';
export default {
  components: {
  LogIn,
  InscripForm,
  Footer,
  }
};
</script>
