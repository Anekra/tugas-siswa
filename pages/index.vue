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
        }
      ]
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
      console.log(data);
    }
  },
  computed: {
    computedData() {
      return this.dataSiswa;
    }
  }
};
</script>
<template>
  <div class="flex flex-col items-center p-16 gap-10 bg-slate-800 min-h-screen">
    <StudentInput @form-siswa="handleFormSiswa" />
    <StudentData :dataSiswa="computedData" />
  </div>
</template>
