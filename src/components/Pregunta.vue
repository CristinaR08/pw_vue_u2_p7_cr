<template>
    <img :src="imagen" alt="No se puede ver">

    <div class="pregunta">
        <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">
        <p>Recuerda que cuando finalices tu pregunta presiona ?</p>
        <h1>{{ pregunta }}</h1>
        <h2>{{ respuesta }}</h2>
    </div>

</template>

<script>

export default {
    data() {
        return {
            pregunta: 'Holi :3',
            respuesta: null,
            imagen: 'https://yesno.wtf/assets/yes/14-b57c6dc03aa15a4b18f53eb50d6197ee.gif',
        };
    },
    watch: {
        pregunta(value, oldValue) {
            console.log(value);
            console.log(oldValue);
            if (value.includes('?')) {
                //programar la llamada al Api para obtener el si o no
                //y la imagenD
                console.log('Aqui llamo al API');
                //this.llamarAPI();
                this.fachada();
            }
        }
    },
    methods: {
        async llamarAPI() {
            const data = await fetch('https://yesno.wtf/api').then(r => r.json());
            this.respuesta = data.answer;
            this.imagen = data.image;
            console.log(data)
        },
        async fachada() {
            await this.llamarAPI();
        }
    }
};
</script>

<style>
img {
    max-height: 100%;
    height: 100vh;
    max-width: 100%;
    width: 100vw;
    position: fixed;
    top: 0px;
    left: 0px;
}

.pregunta {
    position: relative;
}

p,h1, h2{
    color: aliceblue;
    font-weight: bold;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

p{
    font-size: 20px;
    font-style: italic;
}

h2{
    margin-bottom: 5%;
}

input {
margin-top: 35%;
width: 260px;
padding: 15px 30px;
border: none;
border-radius: 7px;
font-size: 18px;
}

</style>