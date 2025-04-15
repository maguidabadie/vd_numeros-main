<script>
  import * as d3 from "d3"
  import Vinilos from "./lib/vinilos.svelte"

  let numbers = [24, 33, 42, 54, 63, 71, 77, 87, 92, 98]

</script>

<main class="container">
  <Vinilos
    numbers={numbers}
  />
  <hr />
</main>


