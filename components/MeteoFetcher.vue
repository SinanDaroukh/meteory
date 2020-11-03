<template>
  <div>
    <v-text-field
      v-model="cityName"
      label="City"
      @keypress.enter="getMeteo"
    ></v-text-field>
    {{ apiData }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      cityName: 'Clermont-Ferrand',
      apiData: [],
    }
  },
  methods: {
    async getMeteo() {
      this.apiData = await fetch(
        'http://api.openweathermap.org/data/2.5/weather?q=' +
          this.cityName +
          '&lang=fr&units=metric&APPID=2d211966188ff1bae767ceb2f358e342'
      ).then((res) => res.json())
    },
  },
}
</script>

<style>
</style>