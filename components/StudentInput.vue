<script>
export default {
  data() {
    return {
      form: {
        noSiswa: null,
        namaSiswa: null,
        nilaiSiswa: null,
      }
    }
  },
  methods: {
    handleSubmit() {
      this.$emit('formSiswa', this.form)
    }
  },
  emits: {
    formSiswa: Object
  }
}
</script>
<template>
  <form v-on:submit.prevent="" class="flex flex-col items-center rounded-lg w-11/12 bg-slate-200 py-5 gap-4">
    <div class="flex justify-between w-10/12 gap-8">
      <div class="flex flex-auto w-1/12 justify-between gap-5">
        <h3 class="xl:text-2xl md:text-lg text-slate-950">No. Induk Siswa</h3>
        <p class="xl:text-2xl md:text-lg text-slate-950">:</p>
      </div>
      <div class="flex-auto w-6/12">
        <input type="number" class="rounded w-full h-full px-2 py-1" v-model="form.noSiswa" required>
      </div>
    </div>
    <div class="flex justify-between w-10/12 gap-8">
      <div class="flex flex-auto w-1/12 justify-between gap-5">
        <h3 class="xl:text-2xl md:text-lg text-slate-950">Nama Siswa</h3>
        <p class="xl:text-2xl md:text-lg text-slate-950">:</p>
      </div>
      <div class="flex-auto w-6/12">
        <input type="text" class="rounded w-full h-full px-2 py-1" v-model="form.namaSiswa" required>
      </div>
    </div>
    <div class="flex justify-between w-10/12 gap-8">
      <div class="flex flex-auto w-1/12 justify-between gap-5">
        <h3 class="xl:text-2xl md:text-lg text-slate-950">Nilai Siswa</h3>
        <p class="xl:text-2xl md:text-lg text-slate-950">:</p>
      </div>
      <div class="flex-auto w-6/12">
        <input type="number" min=0 max=100 class="rounded w-full h-full px-2 py-1" v-model="form.nilaiSiswa" required>
      </div>
    </div>
    <div class="flex justify-center w-9/12 gap-8">
      <div class="flex justify-between gap-5">
        <button @click="handleSubmit" class="rounded-full bg-slate-700 text-slate-300 font-bold px-5 py-1 text-xl hover:bg-slate-400 hover:text-slate-800 hover:outline hover:outline-slate-400 active:bg-blue-300">Submit</button>
        <button class="rounded-full outline border-slate-700 text-slate-700 font-bold px-5 py-1 text-xl hover:bg-slate-500 hover:text-slate-300 hover:outline-none active:bg-gray-400">Cancel</button>
      </div>
    </div>
  </form>
</template>
