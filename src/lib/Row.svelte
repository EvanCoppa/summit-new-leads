<script>
  export let id;
  export let name;
  export let interest;
  export let email;
  export let role;
  export let status = "Active";
  export let index;

  
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();


  function openEditModal() {
    // You can perform any necessary logic here

    // Dispatch a custom event to notify the parent page
    dispatch('openEditModal');
  }

  async function deleteUser() {
    try {
      console.log(id);
      const apiEndpoint = "http://68.183.144.156:5000//remove_lead/" + id; // Replace with your actual API endpoint
      console.log(apiEndpoint);
      // Assuming you have an API key to include in the headers
      const apiKey = "32fd2f32-f0e1-4c1d-aeee-72f7524ad7e2"; // Replace with your actual API key

      const response = await fetch(apiEndpoint, {
        method: "DELETE",
        headers: {
          "Content-Type": "application/json",
          "API-Key": apiKey,
        },
      });

      if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
      }

      const data = await response.json();
      console.log(data);

      dispatch('DeleteUser');
      return data;
    } catch (error) {
      console.error("Error fetching all users:", error.message);
    }
  }
</script>
 <tr
  class="{index % 2 === 0
    ? 'bg-white'
    : 'bg-gray-50'} border-b hover:bg-gray-100"
>
  <td class="w-4 p-4">
    <div class="flex items-center">
      <input
        id="checkbox-table-search-1"
        type="checkbox"
        class="w-4 h-4 bg-red-200 rounded"
      />
      <label for="checkbox-table-search-1" class="sr-only">checkbox</label>
    </div>
  </td>
  <th
    scope="row"
    class="flex items-center px-6 py-4 text-gray-900 whitespace-nowrap"
  >
    <div class="ps-3">
      <div class="text-base font-semibold">{name}</div>
      <div class="font-normal text-gray-500">{email}</div>
    </div>
  </th>
  <td class="px-6 py-4">{role}</td>

  <td class="px-6 py-4">
    <div class="flex items-center">
       {interest}
    </div>
  </td>
  <td class="px-6 py-4">
    <div class="flex items-center">
      <div class="h-2.5 w-2.5 rounded-full bg-green-500 me-2"></div>
      {status}
    </div>
  </td>

  <td class="px-6 py-4">
    <div class="flex gap-4">
      <!-- Modal toggle -->
      <button 
        on:click={openEditModal}
        type="button"
        data-modal-target="editUserModal"
        data-modal-show="editUserModal"
        class="font-medium text-white bg-gray-600 hover:bg-gray-500 rounded-md px-4 py-2"
        >Edit</button>
      <!-- Modal toggle -->
      <button on:click={deleteUser}
        value="{id}"
        type="button"
        data-modal-target="editUserModal"
        data-modal-show="editUserModal"
        class="font-medium text-white bg-red-600 hover:bg-red-500 rounded-md px-4 py-2"
        >Delete</button
      >
      <!-- Modal toggle -->
      <button class=" w-12 bg-gray-100 hover:bg-white rounded-md">
        <img class="w-12"
          src="https://img.icons8.com/fluency-systems-regular/48/clipboard--v1.png"
          alt="clipboard--v1"
        />
      </button>
    </div>
  </td>
</tr>

 