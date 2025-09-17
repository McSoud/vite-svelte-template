<script lang="ts">
  import Input from "@/components/inputs/Input.svelte";
    import Select from "@/components/inputs/Select.svelte";
    import Textarea from "@/components/inputs/Textarea.svelte";
  import Head from "@/components/template/Head.svelte";
</script>

<Head title="Home" />
<main id="home-content">
  <Input name="test" title="Test" type="text" label />
  <Textarea name="test-2" title="Test" label />
  <Select name="test-3" title="Test" label>
    <option value="1">1</option>
    <option value="2">2</option>
  </Select>
</main>
