<script>
  let firstname = "";
  let lastname = "";
  let phonenumber = "";
  let status = "false";
  let email = "";
  let interest = "";
  let addresses = "";

  let showModal = false;
 

  function openModal() {
    showModal = true;
  }

  function closeModal() {
    showModal = false;
  }

  function submitForm() {
    const apiUrl = "http://68.183.144.156:5000"; // Replace with your actual API endpoint
    const apiKey = "32fd2f32-f0e1-4c1d-aeee-72f7524ad7e2"; // Replace with your actual API key

    const userData = {
      firstname,
      lastname,
      phonenumber,
      status,
      email,
      interest,
      addresses,
    };

    const requestOptions = {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        "API-Key": apiKey,
      },
      body: JSON.stringify(userData),
    };

    fetch(`${apiUrl}/add_lead`, requestOptions)
      .then((response) => {
        if (!response.ok) {
          throw new Error(`HTTP error! Status: ${response.status}`);
        }
        return response.json();
      })
      .then((data) => {
        console.log(data); // Handle the response data as needed
        closeModal(); // Close the modal after successful submission
      })
      .catch((error) => {
        console.error("Error:", error);
      });
  }
</script>

<div
  class="flex items-center justify-between flex-column md:flex-row flex-wrap space-y-4 md:space-y-0 py-4 bg-white px-6"
>
  <div>
    <img src="/logo.png" alt="" class="h-12" />

    <div
      id="dropdownAction"
      class="z-10 hidden bg-white divide-y divide-gray-100 rounded-lg shadow w-44"
    >
      <ul
        class="py-1 text-sm text-gray-700"
        aria-labelledby="dropdownActionButton"
      >
        <li>
          <a href="#" class="block px-4 py-2 hover:bg-gray-100">Reward</a>
        </li>
        <li>
          <a href="#" class="block px-4 py-2 hover:bg-gray-100">Promote</a>
        </li>
        <li>
          <a href="#" class="block px-4 py-2 hover:bg-gray-100"
            >Activate account</a
          >
        </li>
      </ul>
      <div class="py-1">
        <a
          href="#"
          class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100"
          >Delete User</a
        >
      </div>
    </div>
  </div>

  <button
    on:click={openModal}
    class="font-medium text-white bg-red-600 hover:bg-red-700 rounded-md px-4 py-2"
  >
    New Lead
  </button>
</div>



{#if showModal}
  <div id="addUserModal" class="">
    
    <form
      id="addUserForm"
      class=" mx-auto p-4 bg-gray-100 border rounded-md shadow-md absolute bg-gray-100 inset-1/2 p-8 transform -translate-x-1/2 -translate-y-3/4 w-1/2 h-1/2"
    >
 
    
      <div class="mx-2 mb-2 float-right">
        <button class="font-bold" on:click={closeModal}>X</button>
      </div>
      <h2 class="text-center font-bold size 5xl mb-4">Add a New Lead</h2>
      <input
        type="text"
        bind:value={firstname}
        id="firstname"
        name="firstname"
        placeholder="First Name"
        required
        class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300"
      />

      <input
        type="text"
        bind:value={lastname}
        id="lastname"
        name="lastname"
        placeholder="Last Name"
        required
        class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300"
      />

      <input
        type="tel"
        bind:value={phonenumber}
        id="phonenumber"
        name="phonenumber"
        placeholder="Phone Number"
        required
        class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300"
      />

      <input
        type="text"
        bind:value={status}
        id="status"
        name="status"
        required
        class="hidden w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300"
      />

      <input
        type="email"
        bind:value={email}
        id="email"
        placeholder="Email"
        name="email"
        required
        class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300"
      />

      <input
        type="text"
        bind:value={interest}
        id="interest"
        placeholder="Interest"
        name="interest"
        required
        class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300"
      />

      <input
        type="addresses"
        bind:value={addresses}
        id="addresses"
        placeholder="Addresse"
        name="interest"
        required
        class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300"
      />

      <!-- <label for="password" class="block mb-1">Password:</label> -->

      <button
        type="button"
        on:click={submitForm}
        class="w-full px-4 py-2 text-white bg-red-500 rounded-md hover:bg-red-600 focus:outline-none focus:shadow-outline-red"
        >Submit</button
      >
    </form>
  </div>
{/if}
