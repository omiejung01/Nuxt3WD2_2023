<template>
    <div class="flex justify-center items-center h-screen " >
        <form id="main_form" action="login_success" method="post"
                  @submit.prevent="signIn" >    
            <div class="w-96 p-6 shadow-lg bg-white rounded-md">
                <h1 class="text-2xl block text-center font-semibold"><i class="fa-solid fa-user"></i>Online Catalog Login</h1>
                <hr class="mt-3">
                <div class="mt-3">
                    <label for="txt_username" class="block text-base mb-2">User</label>
                    <input type="text" id="txt_username"  v-model="user"  class="border w-full text-base px-2 py-1 focus:outline-none focus:ring-0 focus:border-gray-600" placeholder="Enter user" />
                </div>
                <div class="mt-3">
                    <label for="txt_password" class="block text-base mb-2">Password</label>
                    <input type="password" id="txt_password"  v-model="password"  class="border w-full text-base px-2 py-1 focus:outline-none focus:ring-0 focus:border-gray-600" placeholder="Enter password" />
                </div>
                <div class="mt-3 flex justify-between items-center">
                    <div>
                        <!-- <input type="checkbox">
                        <label>Remember Me</label> -->
                    </div>
                    <div>
                        <a href="#" class="text-yellow-800 font-semibold">Forgot Password?</a>
                    </div>
                </div>
                <div class="mt-3 flex justify-between items-center">
                    <div>
    
                    </div>
                    <div>
                        <a href="/register" class="text-yellow-800 font-semibold">Sign up</a>
                    </div>
                </div>
                <div class="mt-5">
                    <button class="border-2 border-green-400 bg-green-300 text-black py-1 w-full rounded-md hover:bg-transparent hover:text-yellow-400 font-semibold"><i class="fa-solid fa-right-to-bracket"></i>&nbsp;&nbsp;Login</button>
                </div>
                <p class="text-red-700" id="error_message">{{ errorMsg }}</p>
                <p class="text-black" id="success_message">{{ successMsg }}</p>
            </div>
        </form>
    </div>
</template>

<script setup lang="ts">
    const user = ref('');
    const password = ref('');
    
    const errorMsg = ref('');
    const successMsg = ref('');
    
    async function signIn() {
      //alert(isAlphanumeric(first_name.value));
    
      //console.log('Email: ' + email.value);
    
        if(await check_input()) {
            var uri = 'https://fuzik03.tetraserver.com/back_login?user=' + user.value +  '&passwd=' + password.value
            
            const response = await fetch(uri);
            const data = await response.json();

            console.log(data.result.localeCompare('Failure'))
            //console.log(uri)
            
            if (data.result.localeCompare('Failure') == 0) {
                errorMsg.value = 'Sorry, cannot Login';
                successMsg.value = "";
                //alert(error.message);
                //throw error;
            } else {
            
                successMsg.value = "Logged in";
                errorMsg.value = "";

                var main_form = <HTMLFormElement>document.getElementById('main_form');

                main_form.submit();
            }
        } 
    
    }
    
    async function check_input() {
        var allowed = false;
     
        if (user.value.length == 0) {
            errorMsg.value = "User cannot be blank.";  
            allowed = false;
        } else if (password.value.length == 0) {    
            errorMsg.value = "Password cannot be blank.";
            allowed = false;
        } else {
            allowed = true;
            errorMsg.value = "";
        }
        return allowed;
    }

    definePageMeta({
        layout: "empty"
    })
</script>

<style scoped>

</style>