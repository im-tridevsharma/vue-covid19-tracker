<template>
  <div class="p-2">
    <select class="bg-blue-light focus:outline-none form-select p-4 w-full mt-5 rounded" v-model="selected">
        <option value="">Select Country</option>
        <option v-for="country in countries" :value="country.ID" :key="country.ID">{{ country.Country }}</option>
    </select>
  </div>
</template>

<script>
export default {
    name: "CountrySelect",
    props:['countries'],
    data(){
      return{
        selected: ''
      }
    },
    watch:{
      selected(){
        const country = this.countries.find(item => item.ID === this.selected)
        this.$emit('get-country', country)
      }
    }
    
}
</script>
