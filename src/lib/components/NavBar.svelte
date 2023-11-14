<script lang="ts">
	import {
		Navbar,
		NavBrand,
		NavLi,
		NavUl,
		NavHamburger,
		Avatar,
		Dropdown,
		DropdownItem,
		DropdownHeader,
		DropdownDivider,
        DarkMode
	} from 'flowbite-svelte';
	import SideBar from './SideBar.svelte';

    export let onClick: (() => void) | undefined; 
</script>

<Navbar>
    <NavHamburger onClick={onClick}></NavHamburger>
	<NavBrand href="/">
		<!-- <img src="/images/flowbite-svelte-icon-logo.svg" class="mr-3 h-6 sm:h-9" alt="Flowbite Logo" /> -->
		<span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">MeasureYourWorld</span>
	</NavBrand>
	<div class="flex items-center md:order-2">
		<Avatar id="avatar-menu" src="/dev/vera2.jpg" class="border-2 border-gray-" />
		<!-- <NavHamburger class1="w-full md:flex md:w-auto md:order-1" /> -->
	</div>
	<Dropdown placement="bottom" triggeredBy="#avatar-menu" open={false}>
		<DropdownHeader>
			<span class="block text-sm">Bonnie Green</span>
			<span class="block truncate text-sm font-medium">name@flowbite.com</span>
		</DropdownHeader>
		<DropdownItem>Dashboard</DropdownItem>
		<DropdownItem>Settings</DropdownItem>
		<DropdownItem> 
                <DarkMode class=""></DarkMode>
        </DropdownItem>
		<DropdownDivider />
		<DropdownItem>Sign out</DropdownItem>
	</Dropdown>
	<!-- <NavUl>
		<NavLi href="/" active={true}>Home</NavLi>
		<NavLi href="/about">About</NavLi>
		<NavLi href="/docs/components/navbar">Navbar</NavLi>
		<NavLi href="/pricing">Pricing</NavLi>
		<NavLi href="/contact">Contact</NavLi>
	</NavUl> -->
</Navbar>

