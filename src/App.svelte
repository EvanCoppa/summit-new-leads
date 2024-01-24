<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Row from './lib/Row.svelte';
</script>

<main class="bg-white w-[100vw]">
  
<div class="relative overflow-x-auto shadow-md sm:rounded-lg w-[900px] h-[100vw] mx-auto">
  <div class="flex items-center justify-between flex-column md:flex-row flex-wrap space-y-4 md:space-y-0 py-4 bg-white px-6">
    <div>
      <img src="/logo.png" alt="" class="h-12">
      <!-- <button id="dropdownActionButton" data-dropdown-toggle="dropdownAction" class="inline-flex items-center text-gray-500 bg-white border border-gray-300 focus:outline-none hover:bg-gray-100 focus:ring-4 focus:ring-gray-200 font-medium rounded-lg text-sm px-3 py-1.5      " type="button">
        <span class="sr-only">Action button</span>
        Action
        <svg class="w-2.5 h-2.5 ms-2.5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 10 6">
          <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 4 4 4-4"/>
        </svg>
      </button> -->
      <!-- Dropdown menu -->
      <div id="dropdownAction" class="z-10 hidden bg-white divide-y divide-gray-100 rounded-lg shadow w-44  ">
        <ul class="py-1 text-sm text-gray-700 " aria-labelledby="dropdownActionButton">
          <li>
            <a href="#" class="block px-4 py-2 hover:bg-gray-100  ">Reward</a>
          </li>
          <li>
            <a href="#" class="block px-4 py-2 hover:bg-gray-100  ">Promote</a>
          </li>
          <li>
            <a href="#" class="block px-4 py-2 hover:bg-gray-100  ">Activate account</a>
          </li>
        </ul>
        <div class="py-1">
          <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100   ">Delete User</a>
        </div>
      </div>
    </div>
    <button class="font-medium text-white bg-red-600 hover:bg-red-700 rounded-md px-4 py-2">New Lead</button>
    <!-- <label for="table-search" class="sr-only">Search</label>
    <div class="relative">
      <div class="absolute inset-y-0 rtl:inset-r-0 start-0 flex items-center ps-3 pointer-events-none">
        <svg class="w-4 h-4 text-gray-500 " aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 20">
          <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"/>
        </svg>
      </div>
      <input type="text" id="table-search-users" class="block pt-2 ps-10 text-sm text-gray-900 border border-gray-300 rounded-lg w-80 bg-gray-50 focus:ring-red-500 focus:border-red-500      " placeholder="Search for users">
    </div> -->
  </div>
  <table class="w-full text-sm text-left rtl:text-right text-gray-500 ">
    <thead class="text-xs text-gray-700 uppercase bg-gray-50  ">
      <tr>
        <th scope="col" class="p-4">
          <div class="flex items-center">
            <input id="checkbox-all-search" type="checkbox" class="w-4 h-4 text-blue-600 bg-gray-100 border-gray-300 rounded focus:ring-red-500    focus:ring-2  ">
            <label for="checkbox-all-search" class="sr-only">checkbox</label>
          </div>
        </th>
        <th scope="col" class="px-6 py-3">
          Name
        </th>
        <th scope="col" class="px-6 py-3">
          Interest
        </th>
        <th scope="col" class="px-6 py-3 w-1/6"> <!-- BEGIN: Added custom width class -->
          Status
        </th>
        <th scope="col" class="px-6 py-3 w-1/6"> <!-- BEGIN: Added custom width class -->
         </th>
        <th scope="col" class="px-6 py-3">
         </th>
      </tr>
    </thead>
    <tbody>
    {#each Array.from({ length: 10 }, (_, i) => i) as index}
      <Row name="Evan Coppa" email="evancoppa@gmail.com" role="Roofing"  status="Called" index={index}/>
    {/each}
    </tbody>
  </table>

</div>

</main>
