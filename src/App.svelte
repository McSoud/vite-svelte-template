<script lang="ts">
  import { Router, Route } from "svelte-routing";
  import Header from "./components/template/Header.svelte";
  import Footer from "./components/template/Footer.svelte";
  import PageHome from "@/pages/home/_index.svelte";
</script>

<Router url="">
  <Header />
  <Route path="/"><PageHome /></Route>
  <Footer />
</Router>
