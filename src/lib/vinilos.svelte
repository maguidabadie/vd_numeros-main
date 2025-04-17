<script>
  import * as d3 from "d3";

  export let numbers = [];
  let reversedNumbers = numbers.slice().reverse();
  // Creamos un nuevo array con la cantidad de elementos en `numbers`
  let countArray = Array.from({ length: numbers.length }, (_, i) => i);

  let altura = d3.scaleLinear().domain([100, 0]).range([600, 150]);
  
  let fondos = d3.scaleLinear().domain([100, 0]).range(["#BFB7F6", "#8C68EE"]);

  let letras = d3.scaleLinear().domain([100, 0]).range(["#FFFCDA", "#F5E56E"]);

  let segundos = d3.scaleLinear().domain([100,0]).range([5, 1]);

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
      title: "Fallen",
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
  <div class="titulo">
    <h3 class="titulo">¿Coinciden las Ventas con el Gusto Joven?</h3>
  </div>

  <div class="espacio1"></div>

  <div class="subtitulo">
    <p class="subtitulo">Los 10 Discos Más Vendidos del Siglo XXI: Éxito comercial vs. valoración generacional.</p>
  </div>

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

         
            <div
              class="imagen"
              style="height: {altura(reversedNumbers[n])}px; width: {altura(reversedNumbers[n])}px; animation-duration:{segundos(reversedNumbers[n])}s"
            >
              <img
                style="height: 100%; width: 100%"
                src={albums[n].img}
                alt={albums[n].title}
                target="_blank"
              />
            </div>
          

        </div>
        <div class="espacio"></div>
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

          
            <div
              class="imagen"
              style="height: {altura(reversedNumbers[n])}px; width: {altura(reversedNumbers[n])}px; animation-duration:{segundos(reversedNumbers[n])}s"
            >
              <img
                style="height: 100%; width: 100%"
                src={albums[n].img}
                alt={albums[n].title}
              />
            </div>
          
        </div>
        <div class="espacio"></div>
        {/if}

      </div>
    {/each}
  </div>

  <div class="segundaparte">
    <div class="espacio"></div>
    <h3 class="subtitulo">Tres formas de <span class="letra">arte,</span> una generación para analizarlas.</h3>
  
    <p class="parrafo2">
      En esta sección comparamos las puntuaciones que jóvenes de 18 a 25 años 
      dieron a los top 10 de discos, libros y películas del siglo XXI.
      A través de visualizaciones, se pueden observar tendencias, contrastes y coincidencias 
      entre los distintos medios. 
      <br />¿Preferimos las historias que se leen, se escuchan o se ven?  
      El análisis busca entender cómo cada expresión artística resuena en la sensibilidad 
      de una generación en constante transformación.
    </p>
  
    <div class="grafico-grande">
      <div class="flourish-embed flourish-chart" data-src="visualisation/22562989">
        <noscript>
          <img src="https://public.flourish.studio/visualisation/22562989/thumbnail" alt="chart visualization" />
        </noscript>
      </div>
    </div>
    <div class="espacio"></div>
    <div class="espacio"></div>
    <p class="subtitulo"> Observemos las direncias de las valoraciones por separado</p>
    <p class="parrafo">
      ¿Qué tan alineados están los gustos de los jóvenes con las ventas globales? <br />
      ¿Qué tipo de arte genera mayor conexión emocional?
    </p>
    <div class="graficos-chicos">
      <div class="flourish-embed flourish-chart" data-src="visualisation/22589612">
        <noscript>
          <img src="https://public.flourish.studio/visualisation/22589612/thumbnail" width="100%" alt="discos" />
        </noscript>
      </div>
      <div class="flourish-embed flourish-chart" data-src="visualisation/22590065">
        <noscript>
          <img src="https://public.flourish.studio/visualisation/22590065/thumbnail" width="100%" alt="libros" />
        </noscript>
      </div>
      <div class="flourish-embed flourish-chart" data-src="visualisation/22589947">
        <noscript>
          <img src="https://public.flourish.studio/visualisation/22589947/thumbnail" width="100%" alt="peliculas" />
        </noscript>
      </div>
      
    </div>
    <div class="parrafo2">
      <p class="parrafo2">
        Los gráficos comparativos muestran un patrón claro: 
        existe una desconexión significativa entre los rankings de prestigio (o ventas) 
        y las preferencias reales de los jóvenes. Aunque el mercado cultural establece ciertos “tops” como referentes universales, 
        la generación de entre 18 y 25 años no siempre comparte esa admiración. <br /></p>
        <ul class="parrafo2">
          <li>En libros, las diferencias son notables especialmente en los primeros puestos. 
            Obras que ocupan el top 1 y top 3 a nivel general, 
            son valoradas con puntajes considerablemente más bajos por los jóvenes. 
            Esto sugiere que los títulos más consagrados no necesariamente representan los intereses de esta generación, 
            que puede estar buscando nuevas voces, temáticas contemporáneas o formatos más accesibles.</li>
          <li>En películas, aunque hay casos donde las valoraciones son similares (especialmente en el top 9 y 10), 
            también se observan grandes brechas en los primeros lugares, 
            lo que podría indicar una saturación frente a clásicos “intocables” y 
            una preferencia por relatos más actuales o que aborden problemáticas con las que los 
            jóvenes se identifican.</li>
          <li>En discos, la tendencia se invierte: los jóvenes valoran mucho más a los álbumes 
            que figuran en el top de ventas que lo que reflejan los rankings comerciales. 
            Esto puede indicar que si bien las ventas responden a un contexto de época, 
            los discos más vendidos siguen resonando emocionalmente en las nuevas generaciones, 
            ganándose un lugar de culto que trasciende lo puramente comercial.</li>
        </ul>
        <p class="parrafo2">En conjunto, estos gráficos refuerzan una idea central del análisis: 
          el éxito comercial o el prestigio histórico no siempre garantizan la conexión emocional 
          con las nuevas generaciones. <br />Mientras que en libros y películas se evidencia una distancia 
          clara entre los rankings tradicionales y las valoraciones jóvenes, en el caso de los discos 
          ocurre lo contrario: los jóvenes parecen revalorizar el canon, asignando puntuaciones 
          incluso más altas que las que figuran en los rankings de ventas. <br />Este hallazgo invita a 
          reflexionar sobre la forma en que se construyen los “tops” culturales y quiénes quedan fuera 
          de esas narrativas dominantes. Al mismo tiempo, pone en valor el rol activo de los jóvenes como
          curadores de su propia cultura, capaces de resignificar el canon con nuevos criterios y sensibilidades. 
        
      </p>
    </div>
    <div class="espacio"></div>
    <div class="subtitulo">
      <p class="subtitulo">¿Qué dice de nuestra generación lo que elegimos escuchar, leer y mirar?</p>
    <div class="espacio"></div>
  </div>

</main>
<footer style="margin-top: 0.25rem; padding: 1rem; font-size: 0.9rem; 
    background-color: #FFFCDA;
    color: #BFB7F6;
    font-family: 'Montserrat', sans-serif;
    margin:0;
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 15px #BFB7F6 ;">
    
  <a href="https://github.com/maguidabadie/vd_numeros-main" target="_blank" style="color: inherit;text-decoration: none">
    Magdalena Dabadie Boyero. Visualización de datos 2025.
  </a>
</footer>
<style>
  
   .albumes{
    display: flex;
    flex-direction: column;
    z-index: -10;
    pointer-events: all;
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

.letra{
  font-family: 'Dancing Script', cursive;
  font-size: 2.7rem;
  color: #2e1a47c0;
  
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
    height: 200px;
    background-color: #FFFCDA;
  }

  .imagen{
    grid-area: vinilo;
    margin-bottom: 1rem;
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
    background-color: #FFFCDA;
    margin: 0;
    text-align: center; 
    color:#2e1a47c0;
    position:relative;
    z-index: -1;
    
  }
  .parrafo {
  font-family: 'Montserrat', sans-serif;
  color: #2e1a47c0;
  background-color: #FFFCDA;
  font-size: 1rem;
  text-align: center;
  margin: 0;
  padding: 2rem;
  gap: 1.5rem;
  position:relative;
  z-index: -1;
  animation: arriba linear both;
  animation-timeline: view();
  animation-range: entry 20% cover 25%;
}
.parrafo2 {
  font-family: 'Montserrat', sans-serif;
  color: #2e1a47c0;
  background-color: #FFFCDA;
  font-size: 1rem;
  text-align: justify;
  margin: 2rem auto;
  padding: 1.5rem 2rem;
  max-width: 1200px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
  position:relative;
  z-index: -1;
  animation: arriba linear both;
  animation-timeline: view();
  animation-range: entry 20% cover 25%;
}

  .espacio{
    height: 30px;
    background-color: #FFFCDA;
  }
  .segundaparte {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem;
    gap: 1.5rem;
    background-color: #FFFCDA;
    border-radius: 1rem;
    max-width: 100%;
    position: relative;
    z-index: -3;
  }

  .subtitulo {
    font-size: 1.8rem;
    font-weight: 600;
    text-align: center;
    color:#2e1a47c0;
  }

  .grafico-grande {
    width: 100%;
    max-width: 750px;
  }

  
  .graficos-chicos {
    display: flex;
    justify-content: space-between;
    gap: 1rem;
    width: 100%;
    flex-wrap: wrap;
    
  }

  .graficos-chicos > div {
    flex: 1 1 300px;
    min-width: 280px;
    max-width: 400px;
  }


</style>
