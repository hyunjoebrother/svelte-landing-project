<script>
  import { Route, Router } from "svelte-routing";
  import MainPage from "./routes/MainPage.svelte";
  export let url = "";
</script>

<Router {url}>
  <Route path="/" component={MainPage} />
</Router>
