<template>
<div>
  <div class="container">
    <div class="row">
      <div class="text-create col-lg-12">
        <h1 class="page-title">Dashboard</h1>
      </div>
      <div class="mt-5 col-lg-12">
        <form role="form" action="#" method="POST" enctype="multipart/form-data">
          <div class="mb-3">
            <label for="exampleInputEmail1" class="form-label" >Product Name</label>
            <input type="text" class="form-control" id="exampleInputEmail1" name="name" placeholder="Enter Product Name" required>
          </div>
          <div class="mb-3">
            <label for="exampleFormControlFile1">Product Image</label><br>
            <input type="file" class="form-control-file" id="exampleFormControlFile1" name="images"
                   accept="image/jpg, image/jpeg, image/png">
            </div>
            <div class="mb-3">
              <label for="exampleInputPassword1" class="form-label" >Product Price</label>
              <input type="text" class="form-control" id="exampleInputPassword1" name="price" placeholder="Enter Product Price">
            </div>
        <button type="submit" class="btn btn-primary">Submit</button>
      </form>
      </div>
      <div class="mt-5 col-lg-12">
        <div>
          <table class="table table-success table-striped">
                <thead>
                  <tr>
                    <th scope="col">ID</th>
                    <th scope="col">Name</th>
                    <th scope="col">Image</th>
                    <th scope="col">Price</th>
                    <th scope="col">Status</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="item in items"
                             :key="item.id">
                    <td scope="row">{{ item.id }}</td>
                    <td scope="row">{{ item.name }}</td>
                    <td scope="row">{{ item.image_id }}</td>
                    <td scope="row">{{ item.price }}</td>
                    <td>
                      <span v-if="task.status == 0" class="badge bg-warning">Inactive</span>
                      <span v-else class="badge bg-success">Active</span>
                    </td>
                  </tr>
                </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</div>
</template>


<script>
  export default {
    name: 'home',
    name: 'dashboard',
    data() {
      return {
        items:[],
      }
    },
    methods: {
      getProduct() {
        this.$axios.get('http://127.0.0.1:8000/api/items').then(response => {
          this.items = response.data;
          console.log(this.items);
        });
      },
    },
  mounted() {
    this.getProduct()
  },

  }
</script>


<style>
  .page-title {
        padding-top: 30px;
        font-size: 34px;
        color: rgb(28, 0, 104);
    }
</style>
