<script>
  let email = "";
  let password = "";
 export let authStatus;

  const handleSubmit = async () => {
    try {
      const apiEndpoint = "http://68.183.144.156:5000/login";

      const apiKey = "32fd2f32-f0e1-4c1d-aeee-72f7524ad7e2"; 

      const response = await fetch(apiEndpoint, {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "API-Key": apiKey,
          username: email,
          password: password,
        },
      });

      if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
      }

      const data = await response.json();

      // Check the response from the server
      if (response.ok) {
        console.log("User authenticated");
        authStatus = true;
        // Redirect to the authenticated page or perform other actions
      } else {
        authStatus = false;
        // Handle authentication failure, show error message, etc.
      }
    } catch (error) {
      console.error("Error during authentication:", error.message);
    }
  };
</script>

<div class="flex">
  <section class="bg-gray-50 w-full">
    <div
      class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0"
    >
      <img class="mb-4 w-32" src="/logo.png" alt="logo" />
      <div class="w-full bg-white rounded-lg shadow md:mt-0 sm:max-w-md xl:p-0">
        <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
          <h1
            class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl"
          >
            Sign in to your account
          </h1>
          <form
            on:submit|preventDefault={handleSubmit}
            class="space-y-4 md:space-y-6"
          >
            <div>
              <label
                for="email"
                class="block mb-2 text-sm font-medium text-gray-900"
                >Username</label
              >
              <input
                bind:value={email}
                type="text"
                name="email"
                id="email"
                class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-red-600 focus:border-red-600 block w-full p-2.5"
                placeholder="username"
              />
            </div>
            <div>
              <label
                for="password"
                class="block mb-2 text-sm font-medium text-gray-900"
                >Password</label
              >
              <input
                bind:value={password}
                type="password"
                name="password"
                id="password"
                placeholder="••••••••••"
                class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-red-600 focus:border-red-600 block w-full p-2.5"
              />
            </div>
            <div class="flex items-center justify-between">
              <a
                href="#"
                class="text-sm font-medium text-red-600 hover:underline"
                >Forgot password?</a
              >
            </div>
            <button
              type="submit"
              class="w-full text-white bg-red-600 hover:bg-red-700 focus:ring-4 focus:outline-none focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center"
              >Sign in</button
            >
          </form>
          {#if authStatus}
            <p>{authStatus}</p>
          {/if}
        </div>
      </div>
    </div>
  </section>
</div>

<style>
  /* Add your styles here */
</style>
