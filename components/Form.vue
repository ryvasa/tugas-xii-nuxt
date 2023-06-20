<template>
  <div
    class="flex flex-row gap-3 border rounded-xl p-5 mt-5 mb-3 bg-base-200 shadow-xl"
  >
    <div class="form-control w-full max-w-xs">
      <label class="label">
        <span class="label-text text-base">Nomor Induk Siswa</span>
      </label>
      <input
        v-model="nis"
        type="number"
        placeholder="No. induk siswa"
        class="input input-bordered w-full max-w-xs"
      />
    </div>
    <div class="form-control w-full max-w-xs">
      <label class="label">
        <span class="label-text text-base">Nama Siswa</span>
      </label>
      <input
        v-model="nama"
        type="text"
        placeholder="Nama siswa"
        class="input input-bordered w-full max-w-xs"
      />
    </div>
    <div class="form-control w-full max-w-xs">
      <label class="label">
        <span class="label-text text-base">Nilai Tugas</span>
      </label>
      <input
        v-model="nilai"
        type="number"
        placeholder="Nilai Tugas"
        class="input input-bordered w-full max-w-xs"
      />
    </div>
    <div class="flex items-end">
      <button
        :class="[
          `btn text-white border-none normal-case`,
          !nis || !nama || nilai.length <= 0
            ? `hover:bg-red-600 bg-red-500`
            : `hover:bg-green-600 bg-green-500`,
        ]"
        @click="
          $emit('addData', { nis, nama, nilai });
          clearForm();
        "
      >
        Tambahkan
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nis: "",
      nama: "",
      nilai: "",
    };
  },
  methods: {
    clearForm: function () {
      this.nis = "";
      this.nama = "";
      this.nilai = "";
    },
  },
};
</script>
<style>
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>
