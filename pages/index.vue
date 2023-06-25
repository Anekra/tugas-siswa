<script>
export default {
  data() {
    return {
      dataSiswa: [
        {
          id: 1,
          noSiswa: 12345,
          namaSiswa: 'Dano',
          nilaiSiswa: 80
        },
        {
          id: 2,
          noSiswa: 12346,
          namaSiswa: 'Lafi',
          nilaiSiswa: 70
        },
        {
          id: 3,
          noSiswa: 12347,
          namaSiswa: 'Saki',
          nilaiSiswa: 90
        },
        {
          id: 4,
          noSiswa: 12348,
          namaSiswa: 'alfi',
          nilaiSiswa: 75
        }
      ],
      searchQuery: ''
    };
  },
  methods: {
    handleFormSiswa(data) {
      this.dataSiswa.push({
        id: this.dataSiswa.length + 1,
        noSiswa: data.noSiswa,
        namaSiswa: data.namaSiswa,
        nilaiSiswa: data.nilaiSiswa
      });
    },
    handleSort(opt) {
      if (opt === 'asc') {
        this.dataSiswa.sort((objOne, objTwo) => {
          const nameA = objOne.namaSiswa.toLowerCase();
          const nameB = objTwo.namaSiswa.toLowerCase();
          if (nameA < nameB) {
            return -1;
          }
          if (nameA > nameB) {
            return 1;
          }
          return 0;
        });
      } else if (opt === 'dsc') {
        this.dataSiswa.sort((objOne, objTwo) => {
          const nameA = objOne.namaSiswa.toLowerCase();
          const nameB = objTwo.namaSiswa.toLowerCase();
          if (nameA < nameB) {
            return 1;
          }
          if (nameA > nameB) {
            return -1;
          }
          return 0;
        });
      }
    },
    handleSearch(query) {
      this.searchQuery = query
    }
  },
  computed: {
    searchedData() {
      if (this.searchQuery) {
        return this.dataSiswa.filter((siswa) => {
          return this.searchQuery
            .toLowerCase()
            .split(' ')
            .every((data) => siswa.namaSiswa.toLowerCase().includes(data));
        });
      } else {
        return this.dataSiswa;
      }
    }
  }
};
</script>
<template>
  <div class="flex flex-col items-center p-16 gap-10 bg-slate-800 min-h-screen">
    <StudentInput @form-siswa="handleFormSiswa" />
    <StudentData :dataSiswa="searchedData" @sort="handleSort" @search="handleSearch" />
  </div>
</template>
