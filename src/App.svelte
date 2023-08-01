<script>
  import { Route, Router } from "svelte-routing";
  import MainPage from "./routes/MainPage.svelte";
  import CanvasPage from "./routes/CanvasPage.svelte";
  export let url = "";
</script>

<Router {url}>
  <Route path="/" component={MainPage} />
  <Route path="/canvas" component={CanvasPage} />
</Router>
