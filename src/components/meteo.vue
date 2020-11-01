<template>
    <div class="container">
        <h1>Ma Météo</h1>

        <div class="form">
            <label for="ville">Votre ville</label>
            <input v-model="ville"  @keypress.enter="appel" id="ville" type="text">
        </div>
        <br>
        <div class="resultatVille" v-if="temps">
            <h2>Votre ville : {{ temps.name }}</h2>
            <div class="card">
                <p>Température : {{ temps.main.temp.toFixed() }} °</p>
                <p>Humidité : {{ temps.main.humidity }} %</p>
                <p>Temps : {{ temps.weather[0].description }}</p>
                <div class="coordonnees">
                    <p>Latitude : {{ temps.coord.lat }} ° </p>
                    <p> Longitude : {{ temps.coord.lon }} °</p>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Meteo',
    data() {
        return {
            ville : '',
            temps: undefined,
            keyApi : 'ffd61b6d805fa19c412962ab4ac6bf92',
            urlApi: 'https://api.openweathermap.org/data/2.5/weather?'
        }
    },
    methods: {
        appel() {
            axios
            .get(`${this.urlApi}q=${this.ville}&units=metric&appid=${this.keyApi}&lang=fr`)
            .then(response => {
                this.temps = response.data;
                console.log(this.temps);
                this.ville = '';
            })
        }
    }

}
</script>

<style scoped>
h1{
    margin-top:30px;
    margin-bottom: 30px;
}
.form{
    max-width: 320px;
    margin:0 auto;
    display: flex;
    flex-direction: column;
    font-size:22px;
}
.form label{
    margin-bottom: 10px;
}
.form input{
    font-size:24px;
    padding: 10px 5px;
    border: none;
    border: 1px solid #333;
    border-radius: 5px;
    outline:none;
    
}
h2{
    margin:20px 0;
}
.coordonnees{
    margin-top: 25px;
}
.card{
    max-width:320px;
    margin: 0 auto 40px;
    padding:30px 10px;
    border:1px solid #333;
    border-radius: 10px;
    font-size: 22px;
}
p{
    margin:10px 0;
}

</style>