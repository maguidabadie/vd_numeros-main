<script>
  import * as d3 from "d3";

  export let numbers = [];
  let reversedNumbers = numbers.slice().reverse();
  // Creamos un nuevo array con la cantidad de elementos en `numbers`
  let countArray = Array.from({ length: numbers.length }, (_, i) => i);

  let altura = d3.scaleLinear().domain([100, 0]).range([600, 150]);
  
  let fondos = d3.scaleLinear().domain([100, 0]).range(["#BFB7F6", "#8C68EE"]);

  let letras = d3.scaleLinear().domain([100, 0]).range(["#FFFCDA", "#F5E56E"]);

  let segundos = d3.scaleLinear().domain([100,0]).range([10,0]);

  let albums = [
    {
      id: "Top 1",
      title: "21",
      artist: "Adele",
      sales: "43 M de ventas",
      img: "./images/viniloadele21.svg",
    },
    {
      id: "Top 2",
      title: "1",
      artist: "The Beatles",
      sales: "33 M de ventas",
      img: "./images/vinilobeatles.svg",
    },
    {
      id: "Top 3",
      title: "Come Away With Me",
      artist: "Norah Jones",
      sales: "28 M de ventas",
      img: "./images/vinilonorah.svg",
    },
    {
      id: "Top 4",
      title: "The Eminem Show",
      artist: "Eminem",
      sales: "28 M de ventas",
      img: "./images/viniloeminem.svg",
    },
    {
      id: "Top 5",
      title: "25",
      artist: "Adele",
      sales: "27 M de ventas",
      img: "./images/viniloadele25.svg",
    },
    {
      id: "Top 6",
      title: "A Rush Of Blood To The Head",
      artist: "Coldplay",
      sales: "23 M de ventas",
      img: "./images/vinilocodplay.svg",
    },
    {
      id: "Top 7",
      title: "Falling",
      artist: "Evanescence",
      sales: "22 M de ventas",
      img: "./images/vinilofalling.svg",
    },
    {
      id: "Top 8",
      title: "Let Go",
      artist: "Avril Lavigne",
      sales: "20 M de ventas",
      img: "./images/viniloavril.svg",
    },
    {
      id: "Top 9",
      title: "Back to Black",
      artist: "Amy Winehouse",
      sales: "20 M de ventas",
      img: "./images/viniloamy.svg",
    },
    {
      id: "Top 10",
      title: "Meteora",
      artist: "Linkin Park",
      sales: "20 M de ventas",
      img: "./images/vinilolinkin.svg",
    },
  ];
</script>

<main id="albumes">
  <div class="albumes1">
    <h3 class="titulo">¿Coinciden las Ventas con el Gusto Joven?</h3>
  </div>

  <div class="espacio1"></div>

  <div class="subtitulo">
    <p class="subtitulo">Los 10 Discos Más Vendidos del Siglo XXI: Éxito comercial vs. valoración generacional.</p>
  </div>
  <div class="espacio"></div>
  <div class="parrafo">
    <p class="parrafo">En esta primera sección exploramos los 10 discos más vendidos del siglo XXI 
    y la puntuación que les asignaron jóvenes de entre 18 y 25 años.<br />
    ¿El álbum más vendido es también el más querido? 
    ¿Qué tan alineados están los charts globales con los gustos de una nueva generación?  </p>
  </div>

  <div class="espacio"></div>

  <div class="albumes">
    {#each countArray as n, i}
      <div class="fondo" style="color:{fondos(reversedNumbers[n])}">

        {#if i%2 == 0}
        <div class="album">
          <div class="texto">
          <div class="Top">
            <p>{albums[n].id}</p>
          </div>

          <div class="nombre" style="color: {fondos(reversedNumbers[n])}">
            <p>{albums[n].title}</p>
            <p class="artist">{albums[n].artist}</p>
            <p class="sales" style="background-color: {fondos(reversedNumbers[n])}; color: {letras(reversedNumbers[n])}">{albums[n].sales}</p>
          </div>

          <div class="puntos">
            <p>{reversedNumbers[n]} pts</p>
          </div>
          </div>

          <div class="imagen" style="height: {altura(reversedNumbers[n])}px; width: {altura(reversedNumbers[n])}px; animation-duration:{segundos(reversedNumbers[n])}s">
            <img
              style="heighy: 100%; width: 100%"
              src={albums[n].img}
              alt={albums[n].title}
            />
          </div>

        </div>
        {:else}
        <div class="album2">
          <div class="texto">
          <div class="Top">
            <p>{albums[n].id}</p>
          </div>

          <div class="nombre" style="color: {fondos(reversedNumbers[n])}">
            <p>{albums[n].title}</p>
            <p class="artist">{albums[n].artist}</p>
            <p class="sales" style="background-color: {fondos(reversedNumbers[n])}; color: {letras(reversedNumbers[n])}">{albums[n].sales}</p>
          </div>

          <div class="puntos">
            <p>{reversedNumbers[n]} pts</p>
          </div>
          </div>

          <div class="imagen" style="height: {altura(reversedNumbers[n])}px; width: {altura(reversedNumbers[n])}px; animation-duration:{segundos(reversedNumbers[n])}s">
            <img
              style="height:100%; width:100%"
              src={albums[n].img}
              alt={albums[n].title}
            />
          </div>
        </div>

        {/if}

      </div>
    {/each}
  </div>
  <div class="segundaparte">
    <div class="espacio"></div>

    <div class="subtitulo">
      <h3 class="subtitulo">Tres formas de arte, una generación para analizarlas.</h3>
    </div>
    <div class="espacio"></div>
    <div class="parrafo">
        <p class="parrafo">En esta sección comparamos las puntuaciones que jóvenes de 18 a 25 años 
          dieron a los top 10 de discos, libros y películas del siglo XXI. <br />
          A través de visualizaciones interactivas, se pueden observar tendencias, contrastes y coincidencias 
          entre los distintos medios. 
          ¿Preferimos las historias que se leen, se escuchan o se ven? ¿Qué formato genera mayor conexión emocional? 
          El análisis busca entender cómo cada expresión artística resuena en la sensibilidad 
          de una generación en constante transformación. </p>
    </div>
    <div class="espacio"></div>


    <div class="grafico">
      <img src="/images/comparacion3.svg" alt="grafico" style="width: 100%;"/>
    </div>
  </div>
</main>

<style>
   .albumes{
    display: flex;
    flex-direction: column;
    z-index: -10;
  }
  .fondo{
    width: 100%;
    background-color:#FFFCDA ;
    position: relative;
    z-index: -10;
    margin: 0;
    padding: 0;
    align-items: center;
    display: flex;
    justify-content: center;
    position: relative;
  }

  .album {
  display: grid;
  grid-template-columns: 1fr auto; /* Dos columnas: info (2fr) y vinilo (1fr) */
  grid-template-rows: auto auto auto;
  grid-template-areas:
    "vinilo texto"
    "vinilo texto";
  gap: 10px;
  padding: 15px;
  justify-content: center; /* Centra horizontalmente el grid */
  align-content: center; 
  position: relative;
  z-index: -9;
  min-width: 1280px;
  background-color: transparent;
  }

  .album2 {
  display: grid;
  grid-template-columns: 1fr auto; /* Dos columnas: info (2fr) y vinilo (1fr) */
  grid-template-rows: auto auto auto;
  grid-template-areas:
    "texto vinilo"
    "texto vinilo";
  gap: 10px;
  padding: 15px;
  justify-content: center; /* Centra horizontalmente el grid */
  align-content: center; 
  position: relative;
  z-index: -9;
  min-width: 1280px;
  background-color: transparent;
  }

  .texto{
    grid-area: texto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto auto auto;
    grid-template-areas: 
    "puntos tops"
    "nombre nombre"
    "nombre nombre";
    place-content: center;
    width: 550px;
  }

  .Top {
  grid-area: tops;
  font-size: 1.7rem;
  color: rgba(58, 46, 95, 0.629);
  z-index: -1;
  position:relative;
  animation: arriba linear both;
  animation-timeline: view();
  animation-range: entry 20% cover 25%;
  font-family: 'Montserrat', sans-serif;
  font-weight: medium;
  justify-items: center;
}

.puntos {
  grid-area: puntos;
  font-size: 2rem;
  color:#5619fdc2 ;
  z-index: -1;
  position:relative;
  animation: arriba linear both;
  animation-timeline: view();
  animation-range: entry 20% cover 25%;
  font-family: 'Montserrat', sans-serif;
  font-weight: bold;
  justify-items: center;
}

.nombre {
  grid-area: nombre;
  font-size: 3rem;
  z-index: -1;
  position:relative;
  animation: arriba linear both;
  animation-timeline: view();
  animation-range: entry 20% cover 25%;
  font-family: 'Montserrat', sans-serif;
  font-weight: bold;
  max-width: 100%;
  overflow: hidden;
  word-wrap: break-word;
}

.artist{
  font-size: 3rem;
  position:relative;
  z-index: -1;
  animation: arriba linear both;
  animation-timeline: view();
  animation-range: entry 20% cover 25%;
  font-family: 'Dancing Script', cursive;
  max-width: 100%;
  overflow: hidden;
  word-wrap: break-word;
}

.sales{
  backdrop-filter: blur(5px);
  font-size: 2rem;
  padding: 10px;
  margin-bottom: 1rem;
  text-align: center;
  z-index: -4;
  position: relative;
  border-radius: 10px;
  font-family: 'Montserrat', sans-serif;
  max-width: 100%;
  overflow: hidden;
  word-wrap: break-word;
    
      animation: arriba linear both;
      animation-timeline: view();
      animation-range: entry 20% cover 25%;

}
  

  @keyframes enhance-header{
    from{
      width: 100%;
      height: 100%;
      background: #BFB7F6;
      position: fixed;
      top: 0;
      left: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      font-family: 'Montserrat', sans-serif;
      font-weight: bold;
      font-size: 3rem;
      color:#2e1a47c7;
      z-index: 3;
    }
    to {
      background: rgba(255,255,255, .4);
      backdrop-filter: blur(5px);
      font-size: 2rem;
      position: fixed;
      padding: 10px;
      margin: 0;
      width: 100%;
      top:0;
      left: 0;
      margin-bottom: 1rem;
      text-align: center;
      font-family: 'Montserrat', sans-serif;
      font-weight: bold;
      color:#2e1a47c0;
      z-index: 3;
    }
  }

  @keyframes rotar {
      to {
        transform: rotate(360deg);
      }
  }
  @keyframes arriba{
    from{
      opacity: 0;
      translate: 0 100px;
      scale: .5;
    }
    to{
      opacity: 1;
      translate: 0 0;
      scale: 1;
    }
  }
  

  .titulo {
    animation: enhance-header linear both;
    animation-timeline: scroll();
    animation-range: 0 150px;
    z-index: 3;
  }

  .espacio1{
    height: 170px;
    background-color: #FFFCDA;
  }

  .imagen{
    grid-area: vinilo;
    margin-bottom: 1rem;
    z-index: -1;
    justify-items: center;
    align-content: center; 
    animation-timing-function: linear;
    animation-name:rotar;
    animation-iteration-count: infinite;
    animation-timeline: visibility;    
    
  }
  .subtitulo{
    font-size: 2rem;
    font-family: 'Montserrat', sans-serif;
    font-weight: bold;
    color:#2e1a47c7 ;
    background-color: #FFFCDA;
    margin: 0;
    text-align: center; /* Centra el texto horizontalmente */
    
  }
  .parrafo{
    font-size: 1;
    font-family: 'Montserrat', sans-serif;
    color:#2e1a47c7 ;
    background-color: #FFFCDA;
    margin: 0;
  }
  .espacio{
    height: 20px;
    background-color: #FFFCDA;
  }

</style>
