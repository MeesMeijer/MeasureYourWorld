<script>
    import "../app.css";

    import NavBar from "$lib/components/NavBar.svelte";
	import SideBar from "$lib/components/SideBar.svelte";

    let hidden = true; 

</script>
  
<NavBar onClick={()=> hidden = !hidden}></NavBar>
<div class="flex ">
    <div class="transition-transform  {hidden ? "-translate-x-full sm:translate-x-0 max-sm:hidden" : ""}">
        <SideBar></SideBar>
    </div>

    <div class="flex-col">
        <div class="">
            <slot/>
        </div>
    </div>
    <!-- <slot></slot> -->
</div>
