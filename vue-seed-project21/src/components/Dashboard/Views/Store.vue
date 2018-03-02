<template>
<div class ="row">

<div class="col-md-12">

<div class="card">
</div>
</div>

<table style="width:100%">
  <tr>
    <th>id</th>
    <th>Name</th>
    <th>Price</th>
    <th>CreatedAt</th>
    <th>UpdatedAt</th>
    <th>SellerName</th>

  </tr>
  <tr v-for="row in items.data">
    <td>{{row._id}}</td>
    <td>{{row.name}}</td>
    <td>{{row.price}}</td>
    <td>{{row.createdAt}}</td>
    <td>{{row.updatedAt}}</td>
    <td>lina</td>
    <button type="Create">Create!</button>
  </tr>
</table>
<!-- <table style="width:100%">
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Price</th>
      <th>CreatedAt</th>
      <th>UpdatedAt</th>
      <th>sellername</th>
    </tr>

    <tr v-for="row in rows.data">
      <td>{{row.id}}</td>
      <td>{{row.name}}</td>
      <td>{{row.Price}}</td>
      <td>{{row.CreatedAt}}</td>
      <td>{{row.UpdatedAt}}</td>
      <td>{{row.sellername}}</td>
    </tr>

</table> -->

</div>
</template>
<script>
import axios from 'axios'
import PaperTable from 'components/UIComponents/PaperTable.vue'
const tableColumns = ['Id', 'Name', 'Price', 'CreatedAt', 'UpdatedAt', 'SellerName', 'Action', '']
const tableData = [{
  id: 1,
  name: 'Dakota Rice',
  price: '$36.738',
  createdat: '15/2/2018',
  updatedat: '16/2/2018',
  sellername: 'Mo'
},
{
  id: 2,
  name: 'Minerva Hooper',
  price: '$36.738',
  createdat: '15/2/2018',
  updatedat: '16/2/2018',
  sellername: 'Mo'
}]
export default {
  components: {
    PaperTable
  },
  data () {
    return {
      table1: {
        title: 'Stripped Table',
        subTitle: 'Here is a subtitle for this table',
        columns: [...tableColumns],
        data: [...tableData]
      },
      table2: {
        title: 'Table on Plain Background',
        subTitle: 'Here is a subtitle for this table',
        columns: [...tableColumns],
        data: [...tableData]
      },
      items: []
    }
  },
  created () {
    this.getProducts()
  },
  methods: {
    AddToApi () {
      let newtable = {
        tablecolumns: this.table1.tableColumns,
        tabledata: this.table1.tableData
      }
      axios.post('http://localhost:3000/User')
    .then((response) => {
      console.log(response)
    })
    .catch((error) => {
      console.log(error)
    })
    },
    getProducts () {
      axios.get('http://localhost:3000/api/product/getProducts')
    .then((response) => {
      this.items = response.data
      console.log(response)
    })
    .catch((error) => {
      console.log(error)
    })
    },
    createProducts () {
      axios.get('http://localhost:3000/api/product/createProducts', {
        name: this.Name,
        price: this.Price
      })
  .then((response) => {
    this.items = response.data
    console.log(response)
  })
  .catch((error) => {
    console.log(error)
  })
    }
  }
}
</script>
<style>

</style>
