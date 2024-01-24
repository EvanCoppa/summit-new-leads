<script>
    export let name;
    export let email;
    export let role;
    export let status;
    export let index;
</script>


<tr class="{index % 2 === 0 ? 'bg-white' : 'bg-gray-50'} border-b hover:bg-gray-100 ">
    <td class="w-4 p-4">
        <div class="flex items-center">
            <input id="checkbox-table-search-1" type="checkbox" class="w-4 h-4 bg-red-200 rounded ">
            <label for="checkbox-table-search-1" class="sr-only">checkbox</label>
        </div>
    </td>
    <th scope="row" class="flex items-center px-6 py-4 text-gray-900 whitespace-nowrap">
        <div class="ps-3">
            <div class="text-base font-semibold">{name}</div>
            <div class="font-normal text-gray-500">{email}</div>
        </div>
    </th>
    <td class="px-6 py-4">{role}</td>


    <td class="px-6 py-4">
        <div class="flex items-center">
            <div class="h-2.5 w-2.5 rounded-full bg-green-500 me-2"></div> {status}
        </div>
    </td>
    <td class="px-6 py-4">
        <!-- Modal toggle -->
        <button type="button" data-modal-target="editUserModal" data-modal-show="editUserModal" class="font-medium text-white bg-gray-600 hover:bg-red-700 rounded-md px-4 py-2">Edit user</button>
    </td>
    <td class="px-6 py-4">
        <!-- Modal toggle -->
        <button type="button" data-modal-target="editUserModal" data-modal-show="editUserModal" class="font-medium text-white bg-red-600 hover:bg-red-700 rounded-md px-4 py-2">Delete user</button>
    </td>
</tr>