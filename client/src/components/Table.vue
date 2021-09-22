<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-10">
        <h1>Some table</h1>
        <hr><br><br>
        <button type="button" class="btn btn-success btn-sm">Add Entry</button>
        <br><br>
        <table class="table table-hover">
          <thead>
            <tr>
              <th scope="col">Дата</th>
              <th scope="col">Название</th>
              <th scope="col">Количество</th>
              <th scope="col">Расстояние</th>
              <th></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(row, index) in table" :key="index">
              <td>{{ row.date }}</td>
              <td>{{ row.title }}</td>
              <td>{{ row.amount }}</td>
              <td>{{ row.distance }}</td>
              <td>
                <div class="btn-group" role="group">
                  <button type="button" class="btn btn-warning btn-sm">Update</button>
                  <button type="button" class="btn btn-danger btn-sm">Delete</button>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      table: [],
    };
  },
  methods: {
    getBooks() {
      const path = 'http://localhost:5000/table';
      axios.get(path)
        .then((res) => {
          this.table = res.data.table;
        })
        .catch((error) => {
          // eslint-disable-next-line
          console.error(error);
        });
    },
  },
  created() {
    this.getBooks();
  },
};
</script>
