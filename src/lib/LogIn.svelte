<script>
    let auth = false; // Initially, set auth to false
  
    const handleSubmit = async (event) => {
      event.preventDefault(); // Prevents the default form submission and page reload
  
    
      try {
        const apiEndpoint = "http://68.183.144.156:5000/login"; // Replace with your actual API endpoint
  
        // Assuming you have an API key to include in the headers
        const apiKey = "32fd2f32-f0e1-4c1d-aeee-72f7524ad7e2"; // Replace with your actual API key
  
        const response = await fetch(apiEndpoint, {
          method: "GET",
          headers: {
            "Content-Type": "application/json",
            "API-Key": apiKey,
            "username": "",
            "password": "admin"
          },
        });
  
        if (!response.ok) {
          throw new Error(`HTTP error! Status: ${response.status}`);
        }
  
        const data = await response.json();      
        return data;
      } catch (error) {
        console.error("Error fetching all users:", error.message);
      }
    };
    
  </script>



<div class="flex">
    <section class="bg-gray-50 w-full">
        <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0">
                 <img class="mb-4 w-32" src="/logo.png" alt="logo">
             <div class="w-full bg-white rounded-lg shadow  md:mt-0 sm:max-w-md xl:p-0  ">
                <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
                    <h1 class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl ">
                        Sign in to your account
                    </h1>
                    <form class="space-y-4 md:space-y-6" action="#">
                        <div>
                            <label for="email" class="block mb-2 text-sm font-medium text-gray-900 ">Your email</label>
                            <input type="email" name="email" id="email" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-red-600 focus:border-red-600 block w-full p-2.5      " placeholder="name@summitexteriors.org">
                        </div>
                        <div>
                            <label for="password" class="block mb-2 text-sm font-medium text-gray-900 ">Password</label>
                            <input type="password" name="password" id="password" placeholder="••••••••••" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-red-600 focus:border-red-600 block w-full p-2.5      ">
                        </div>
                        <div class="flex items-center justify-between">
                            <!-- <div class="flex items-start">
                                <div class="flex items-center h-5">
                                  <input id="remember" aria-describedby="remember" type="checkbox" class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-red-300    " required="">
                                </div>
                                <div class="ml-3 text-sm">
                                  <label for="remember" class="text-gray-500 ">Remember me</label>
                                </div>
                            </div> -->
                            <a href="#" class="text-sm font-medium text-red-600 hover:underline ">Forgot password?</a>
                        </div>
                        <button type="submit" class="w-full text-white bg-red-600 hover:bg-red-700 focus:ring-4 focus:outline-none focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center   ">Sign in</button>
                        <!-- <p class="text-sm font-light text-gray-500 ">
                            Don’t have an account yet? <a href="#" class="font-medium text-red-600 hover:underline ">Sign up</a>
                        </p> -->
                    </form>
                </div>
            </div>
        </div>
      </section>

</div>