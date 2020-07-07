<template>
    <v-container fluid ma-0 pa-4 mb-4 grid-list-xl primary>
      <v-layout row wrap>
          <v-flex
            v-for="item in info"
            :key="item.fecha"
            :cols="3"
            xs12 sm12 md12 lg12
          >
            <v-card>
                <v-img
                  class="white--text align-end"
                  height="200px"
                  src="https://picsum.photos/200/300?grayscale"
                  id=""
                >
                  <v-card-title>Sismo {{ item.Magnitud }}</v-card-title>
                </v-img>

                <v-card-subtitle class="pb-0">
                  Fecha: {{ item.Fecha }}
                </v-card-subtitle>

                <v-card-subtitle>
                  {{ item.RefGeografica }}
                </v-card-subtitle>

                <v-card-text class="text--primary pb-0">
                  <span>Magnitud: {{ item.Magnitud }}</span>
                </v-card-text>

                <v-card-text class="text--primary pb-0">
                  <span>Longitud: {{ item.Longitud }}</span>
                </v-card-text>

                <v-card-text class="text--primary pb-0">
                  <span>Latitud: {{ item.Latitud }}</span>
                </v-card-text>

                <v-card-actions>
                  <v-flex>
                    <v-btn
                      class="ma-1"
                      color="green"
                      outlined
                      rounded
                    >
                    Compartir
                    <v-icon right>mdi-whatsapp</v-icon>
                    </v-btn>

                    <v-btn
                      class="ma-1"
                      color="red"
                      outlined
                      rounded
                    >
                    Ir a Google Maps
                    <v-icon right>mdi-google-maps</v-icon>
                    </v-btn>
                  </v-flex>

                </v-card-actions>
              </v-card>
          </v-flex>
      </v-layout>
    </v-container>
</template>

<script>



    import axios from "axios"

    export default {
        name: 'ImageCard',
        data () {
            return {
                info: null,
                loading: true,
                errored: false
            }
        },
        mounted () {

            let vue = this;

            axios.get('https://api.gael.cl/general/public/sismos')
            .then(response => {
                vue.info = response.data
            })
            .catch(error => {
                vue.errored = true
            })
            .finally(() => this.loading = false)
        }
    }
    
</script>
