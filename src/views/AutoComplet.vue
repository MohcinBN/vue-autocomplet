<template>
  <div class="about flex flex-col items-center">
    <h1>Search chnage hhhhhhhhhhhhhhhh</h1>

    <div class="container mx-auto px-4">
      <input class="bg-gray-400 rounded py-2 px-4 w-24 w-1/2" type="text"
      autocomplete="off"
      v-model="city"
      @input="filterCities"
      @focus="selected = true"
      >

      <div v-if="citiesToBoFiltred && selected">
        <ul class="bg-gray-800 w-1/2 mx-auto text-white border-b-white cursor-pointer">
          <li v-for="city in citiesToBoFiltred" v-bind:key="city" @click="selectCity(city)">
            {{ city }}
          </li>
        </ul>
      </div>
    </div>
    

  </div>
</template>

<script>
export default {
  data() {
    return {
      city: '',
      selected: false,
      cities: [
        'Rabat', 'Sale', 'Khemisset', 'Tanger', 'Maaziz', 'Tatouan', 'Casablanca', 'Kenitra', 'Agadir',
      ],
      // to target lowercase ..
      citiesToBoFiltred: [],
    }
  },

  mounted() {
    // initial state
    this.filterCities();
  },


  methods: {
      filterCities() {
        // show the user all cities..
        if (this.city.length == 0) {
          this.citiesToBoFiltred = this.city;
        }

        this.citiesToBoFiltred = this.cities.filter(city =>{
          return city.toLowerCase().startsWith(this.city.toLowerCase());
        })
      },

      selectCity(city){
        this.city = city;
        this.selected = false;
      },

  }
}
</script>