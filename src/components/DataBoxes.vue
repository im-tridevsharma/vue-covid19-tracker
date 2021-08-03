<template>
  <div class="grid gap-4">
      <!-- box1 -->
      <div class="bg-blue-light p-10 shadow-md text-center rounded m-2">
          <h3 class="text-2xl mb-4">Cases</h3>
          <div class="mb-4">
              <span class="font-bold">New:</span>
              {{ numberWithCommas(stats.NewConfirmed) }}
          </div>
          <div class="mb-4">
              <span class="font-bold">Confirmed:</span>
              {{ numberWithCommas(stats.TotalConfirmed) }}
          </div>
      </div>
      <!-- box2 -->
      <div class="bg-green-light p-10 shadow-md text-center rounded m-2">
          <h3 class="text-2xl mb-4">Recovered</h3>
          <div class="mb-4">
              <span class="font-bold">New:</span>
              {{ numberWithCommas(stats.NewRecovered) }}
          </div>
          <div class="mb-4">
              <span class="font-bold">Confirmed:</span>
              {{ numberWithCommas(stats.TotalRecovered) }}
          </div>
      </div>
      <!-- box3 -->
      <div class="bg-red-light p-10 shadow-md text-center rounded m-2">
          <h3 class="text-2xl mb-4">Deaths</h3>
          <div class="mb-4">
              <span class="font-bold">New:</span>
              {{ numberWithCommas(stats.NewDeaths) }}
          </div>
          <div class="mb-4">
              <span class="font-bold">Confirmed:</span>
              {{ numberWithCommas(stats.TotalDeaths) }}
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: "DataBoxes",
    props:['stats'],
    methods:{
        numberWithCommas( number ){
            return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        }
    }
}
</script>
<style scoped>
.grid{
    display: grid;
    grid-auto-flow: column;
}
@media screen and (max-width:768px){
    .grid{
        grid-auto-flow: row;
    }
}
</style>
