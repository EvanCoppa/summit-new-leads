<script>
  // @ts-nocheck

  // import svelteLogo from "./assets/svelte.svg";
  import viteLogo from "/vite.svg";
  import Row from "./Row.svelte";
  import Nav from "../componets/Nav.svelte";

  var users = [];
  var firstname = "";
  var lastname = "";
  var email = "";
  var interest = "";
  var status = "";
  var phonenumber = "";


  let showEditModal = false;

  function openEditModal(data) {
    firstname = data[1];
    lastname = data[2];
    email = data[4];
    interest = data[6];
    status = data.status;
    phonenumber = data[5];
    showEditModal = true;
    console.log(data);
  }

  function closeEditModal() {
    console.log("Edit modal closed");
    showEditModal = false;
  }

  function handleOpenEditModal() {
    // Handle the openEditModal event here
    console.log('Edit modal opened sdfdasf');
  }

  async function getAllUsers() {
    try {
      const apiEndpoint = "http://68.183.144.156:5000/test"; // Replace with your actual API endpoint

      // Assuming you have an API key to include in the headers
      const apiKey = "32fd2f32-f0e1-4c1d-aeee-72f7524ad7e2"; // Replace with your actual API key

      const response = await fetch(apiEndpoint, {
        method: "GET",
        headers: {
          "Content-Type": "application/json",
          "API-Key": apiKey,
        },
      });

      if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
      }

      const data = await response.json();
      // console.log("All users:", data);

      console.log(data["users"]);
      users = data["users"];

      return data;
    } catch (error) {
      console.error("Error fetching all users:", error.message);
    }
  }

  // Example usage:
  getAllUsers();
  // var json_data = getAllUsers();
  // var result = [];
  // for (var i in json_data) result.push([i, json_data[i]]);
  // console.log(result);
</script>

<div class="relative overflow-x-auto shadow-md sm:rounded-lg h-[100vw] mx-auto">
  <Nav />
  <table class="w-full text-sm text-left rtl:text-right text-gray-500">
    <thead class="text-xs text-gray-700 uppercase bg-gray-50">
      <tr>
        <th scope="col" class="p-4">
          <div class="flex items-center">
            <input
              id="checkbox-all-search"
              type="checkbox"
              class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-red-500 focus:ring-2"
            />
            <label for="checkbox-all-search" class="sr-only">checkbox</label>
          </div>
        </th>
        <th scope="col" class="px-6 py-3"> Name </th>
        <th scope="col" class="px-6 py-3"> Phone Number </th>
        <th scope="col" class="px-6 py-3"> Interest </th>

        <th scope="col" class="px-6 py-3 w-1/6">
          <!-- BEGIN: Added custom width class -->
          Status
        </th>
        <th scope="col" class="px-6 py-3 w-1/6">
          <!-- BEGIN: Added custom width class -->
        </th>
      </tr>
    </thead>
    <tbody>
      {#each users as user, $index (user)}
        <Row on:openEditModal={() => openEditModal(user)}
          name={user[1] + " " + user[2]}
          email={user[4]}
          role={user[3]}
          interest={user[6]}
          status={user.status}
          index={$index}
          id={user[0]}
        />
      {/each}
    </tbody>
  </table>
</div>

{#if showEditModal}
<div class="flex flex-col p-4 bg-gray-100 border rounded-md shadow-md absolute bg-gray-100 inset-1/2 p-8 transform -translate-x-1/2 -translate-y-3/4 w-1/2 h-[60%]">
  <div class="mx-2 mb-2 float-right">
    <button class="font-bold float-right" on:click={closeEditModal}>X</button>
  </div>
  <h2 class="text-center font-bold size 5xl mb-4">Edit {firstname}'s Information</h2>
  <form action="" class="flex flex-col">
    <input type="text" value={firstname} class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300">
    <input type="text" value={lastname} class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300">
    <input type="text" value={email} class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300">
    <input type="text" value={phonenumber} class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300">
    <input type="text" value={status} class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300">
    <input type="text" value={interest} class="w-full px-3 py-2 mb-4 leading-tight border rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300">
    <button class="w-full px-4 py-2 text-white bg-red-500 rounded-md hover:bg-red-600 focus:outline-none focus:shadow-outline-red mb-12"    >Save</button>
  

  </form>
  
</div>
   
 {/if}
