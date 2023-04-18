<script>
const API_URL = 'https://api.openweathermap.org/data/2.5/forecast?lat=42.9849&lon=-81.2453&appid=74f520ff87f8ff10000abb40242d5d46&units=metric'

export default {
    data: ()=> ({
        myTS: null,
        condition: null,
        temperature: null,
    }),
    created(){
        this.fetchData()
    },
    methods: {
        async fetchData(){
            const url = `${API_URL}`
            const res = await (await fetch(url)).json() 
            this.myTS = res.list[0].dt;
            this.condition = res.list[0].weather[0].description;
            this.temperature = res.list[0].main.temp;
            console.log(res);
        },
    }
 }
 </script>

 <template>
  <div id="w-header">Prediction's timestamp: {{ myTS }}</div>
  <div id="w-condition">Condition: {{ condition }}</div>
  <div id="w-temperature">Temperature: {{ temperature }}</div>  
 </template>

 <style>

</style>