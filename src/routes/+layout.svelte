<script>
    import "../app.css";

    import NavBar from "$lib/components/NavBar.svelte";
	import SideBar from "$lib/components/SideBar.svelte";

    let hidden = true; 

</script>
  
<NavBar onClick={()=> hidden = !hidden}></NavBar>
<div class="flex flex-row">
    <div class="transition-transform   {hidden ? "-translate-x-full sm:translate-x-0 max-sm:hidden" : ""}">
        <SideBar></SideBar>
    </div>

    <div class="flex">
        <slot/>
    </div>
    <!-- <slot></slot> -->
</div>
