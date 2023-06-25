<script>
export default {
  data() {
    return {
      searchQuery: ''
    }
  },
  props: {
    dataSiswa: Array
  },
  methods: {
    onSelectChanged(opt) {
      this.$emit('sort', opt.target.value);
    },
    onSearchClicked() {
      this.$emit('search', this.searchQuery)
    }
  },
  emits: {
    sort: '',
    search: ''
  }
};
</script>

<template>
  <div
    class="flex flex-col items-center rounded-lg w-11/12 bg-slate-200 py-5 px-5 gap-4 h-full"
  >
    <div class="w-full flex gap-10">
      <h1 class="text-2xl">Data Siswa</h1>
      <select
        @change="onSelectChanged"
        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 p-2 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
      >
        <option disabled selected>Sort by</option>
        <option value="asc">Nama siswa (asc)</option>
        <option value="dsc">Nama siswa (dsc)</option>
      </select>
      <div class="relative text-gray-600">
        <input
          type="text"
          placeholder="Search ..."
          v-model="searchQuery"
          class="bg-white h-10 px-5 pr-10 rounded-full text-sm focus:outline-none"
        />
        <button type="submit" @click="onSearchClicked" class="absolute right-0 top-0 mt-3 mr-4">
          <svg
            class="h-4 w-4 fill-current"
            xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink"
            version="1.1"
            id="Capa_1"
            x="0px"
            y="0px"
            viewBox="0 0 56.966 56.966"
            style="enable-background: new 0 0 56.966 56.966"
            xml:space="preserve"
            width="512px"
            height="512px"
          >
            <path
              d="M55.146,51.887L41.588,37.786c3.486-4.144,5.396-9.358,5.396-14.786c0-12.682-10.318-23-23-23s-23,10.318-23,23  s10.318,23,23,23c4.761,0,9.298-1.436,13.177-4.162l13.661,14.208c0.571,0.593,1.339,0.92,2.162,0.92  c0.779,0,1.518-0.297,2.079-0.837C56.255,54.982,56.293,53.08,55.146,51.887z M23.984,6c9.374,0,17,7.626,17,17s-7.626,17-17,17  s-17-7.626-17-17S14.61,6,23.984,6z"
            />
          </svg>
        </button>
      </div>
    </div>
    <div class="w-full h-full rounded-lg bg-slate-800">
      <table class="table-auto border-collapse w-full text-slate-300 h-full">
        <thead>
          <tr>
            <th class="border border-slate-300 py-2">No. Induk Siswa</th>
            <th class="border border-slate-300 py-2">Nama Siswa</th>
            <th class="border border-slate-300 py-2">Nilai Siswa</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="siswa in dataSiswa" :key="dataSiswa.id">
            <td class="border border-slate-300 px-2 py-1">
              {{ siswa.noSiswa }}
            </td>
            <td class="border border-slate-300 px-2 py-1">
              {{ siswa.namaSiswa }}
            </td>
            <td class="border border-slate-300 px-2 py-1">
              {{ siswa.nilaiSiswa }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
