<template>
  <div class="mt-5 border rounded-xl shadow-xl p-3">
    <div class="my-3">
      <p class="text-base">
        Nilai rata-rata : <b>{{ avg }}</b>
      </p>
    </div>
    <div class="overflow-x-auto rounded-xl">
      <table class="table text-base">
        <thead>
          <tr class="text-base bg-base-200">
            <th>ID</th>
            <th class="text-base">NIS</th>
            <th class="text-base">Nama</th>
            <th class="text-base">Nilai</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item of data" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.nis }}</td>
            <td>{{ item.nama }}</td>
            <td>{{ item.nilai }}</td>
            <td>
              <button
                @click="$emit('deleteData', item.id)"
                class="btn hover:bg-red-600 bg-red-500 text-white btn-xs border-none normal-case"
              >
                Hapus
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
  computed: {
    avg() {
      if (this.data.length > 0) {
        const sum = this.data.reduce((sum, item) => sum + item.nilai, 0);
        return sum / this.data.length;
      } else {
        return 0;
      }
    },
  },
};
</script>
