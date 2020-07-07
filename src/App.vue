<template>

  <v-app>
    <v-main>
      <AppBar/>
      <Titulo/>
      <ImageCard/>
    </v-main>
    <Footer/>
  </v-app>
</template>

<script>


import Titulo from './components/Titulo';
import AppBar from './components/AppBar';
import ImageCard from './components/ImageCard';
import Footer from './components/Footer';

export default {
  name: 'App',

  components: {
    Titulo,
    AppBar,
    ImageCard,
    Footer
  },

  data: () => ({
    //
  }),
};
</script>
