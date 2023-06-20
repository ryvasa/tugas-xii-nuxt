<template>
  <div class="w-full justify-center items-center flex">
    <div class="w-10/12">
      <Form @add-data="addData" />
      <Data :data="dataSiswa" @delete-data="deleteData" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dataSiswa: [],
    };
  },
  methods: {
    addData(data) {
      if (!data.nis || !data.nama || !data.nilai.length <= 0) {
        alert("Data tidak lengkap, mohon isi semua form");
      } else {
        data = { ...data, id: Date.now() };
        this.dataSiswa.unshift(data);
      }
    },
    deleteData(id) {
      this.dataSiswa = this.dataSiswa.filter((item) => item.id !== id);
    },
  },
};
</script>
