<template>
  <div id="app" class="container py-3">
    <div class="mb-3">
      <label class="mb-1">Choose CSV</label>
      <input type="file" class="form-control" />
    </div>

    <template v-if="fileLoaded">
      <div class="mb-3">
        <label class="mb-1">Table column (JSON Array)</label>
        <input class="form-control" v-model="columnsJson" />
      </div>

      <div class="mb-3">
        <label class="mb-1">Barcode column</label>
        <select class="form-control">
          <option value="" disabled selected hidden></option>
          <option v-for="column in columns" :key="column">{{ column }}</option>
        </select>
      </div>

      <table class="table table-bordered table-striped">
        <thead>
          <tr>
            <th v-for="column in columns" :key="column">{{ column }}</th>
          </tr>
        </thead>

        <tbody>
          <tr v-for="(row, i) in data" :key="i">
            <td v-for="column in columns" :key="column">{{ row[column] }}</td>
          </tr>
        </tbody>
      </table>
    </template>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      data: [],
      columns: [],
      columnsJson: "[]",
      fileLoaded: false,
    };
  },
  components: {},
};
</script>

<style>
#app {
}
</style>
