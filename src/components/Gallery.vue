<template>
  <v-container>
    <div class="pa-6 text-center">
      Galeria
    </div>
       <v-row>
      <v-col cols="6" md="3" sm="4" lg="2" v-for="(photo, index) in photos" :key="photo.id">
          <show-image :photo="photo" @remove="remove(index)">
          </show-image>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
const axios = require('axios').default;

import ShowImage from './ShowImage.vue'
  export default {
    components: { ShowImage },
    name: "GalleryTest",
    data() {
      return{
        gallery: [],
        photos: [],
        counter: 0,
      }
    },
    mounted () {
      this.getPhotos()
    },

    methods:{
      scroll () { //detecto el final del scroll para cargar mas imagenes
        window.onscroll = () => {        
          let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight === document.documentElement.offsetHeight
          if (bottomOfWindow) {
           this.loadPhotos()
          }
        };
      },
      async getPhotos() { //cargamos la galeria
        await axios.get('https://jsonplaceholder.typicode.com/photos').then(response => {
          if(response.data.lenght!==0){
            this.gallery=response.data
               this.loadPhotos()
          }
          this.scroll()
        })
      },
      loadPhotos() {  //cargamos las imagenes de 41 en 41
        let elementsToCharge = 0
        if((this.counter+41) <= this.gallery.length){ //si no me salgo del limite del array cargo 41 fotos mas
          elementsToCharge = this.counter + 41
        }else{  // si me salgo del array cargo los elementos restantes
          elementsToCharge = this.gallery.length-this.counter-1
        }
        for(this.counter; this.counter<= elementsToCharge; this.counter++){ //cargo los elementos a mostrar
          this.photos.push(this.gallery[this.counter])
        }      
      },
      remove(item){ //eliminamos el elemento del array
        this.photos.splice(item,1)
        if(this.photos.length <= 41) {  //en caso que el numero de elementos sea menor que x cargo mas elementos automaticamente
          this.loadPhotos()
        }
      }
    }
}
</script>
<style scoped>

</style>
