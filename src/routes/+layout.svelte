<script>
  import NavBar from "../components/NavBar.svelte";
  import FootBar from "../components/FootBar.svelte";
</script>

<div class="flex flex-col w-full h-full justify-between bg-sky-50">

    <div class="flex flex-col">
        <NavBar />
        <div class="h-fit mt-20 pb-5 pt-20 ">

            <slot />
        </div>
    </div>
    <FootBar />
</div>
