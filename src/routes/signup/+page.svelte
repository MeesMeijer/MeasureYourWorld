<script>
	import { Card, Button, Label, Input, Checkbox } from 'flowbite-svelte';
</script>


<div class="">
    <div class="grid col-start-2 w-full max-w-md ">
        <form class="flex flex-col space-y-6" action="/">
            <h3 class="text-xl font-medium text-gray-900 dark:text-white">Register to our platform</h3>
            <Label class="space-y-2">
                <span>Email</span>
                <Input type="email" name="email" placeholder="name@company.com" required />
            </Label>
            <Label class="space-y-2">
                <span>Your password</span>
                <Input type="password" name="password" placeholder="•••••" required />
            </Label>
            <div class="flex items-start">
                <Checkbox>Remember me</Checkbox>
            </div>
            <Button type="submit" class="w-full" color={"blue"}>Register</Button>
            <div class="text-sm font-medium text-gray-500 dark:text-gray-300">
                Already have an account? <a href="../signin" class="text-blue-700 hover:underline dark:text-blue-500">
                    Login
                </a>
            </div>
        </form>
    </div>
</div>