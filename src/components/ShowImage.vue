<template>
  <div>
    <v-tooltip bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-img
            v-bind="attrs"
            v-on="on"
            max-height="150"
            max-width="250"
            :src="photo.url"
            @click="$emit('remove',photo)"
          ></v-img>
        </template>
        <span>title: {{photo.title}}</span>
      </v-tooltip>
  </div>
</template>

<script>
export default {
    name: "ShowImage",
    props:{
      photo:{
        type: Object,
        required: false
      }
    }

}
</script>

<style>

</style>