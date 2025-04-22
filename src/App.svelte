<script lang="ts">
  import { Router, Route } from "svelte-routing";
  import Header from "./lib/components/template/Header.svelte";
  import PageHome from "@/lib/pages/home/_index.svelte";
  import Footer from "./lib/components/template/Footer.svelte";
</script>

<Router url="">
  <Header />
  <Route path="/"><PageHome /></Route>
  <Footer />
</Router>
