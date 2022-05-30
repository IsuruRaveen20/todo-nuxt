<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-lg-12 text-center">
          <h1 class="page-title">Products</h1>
        </div>
        <div>
          <form action="#" method="post" enctype="multipart/form-data">
            <!-- @csrf -->
            <div class="mb-3">
              <label for="productName" class="form-label">Product Name</label>
              <input type="text" name="name" class="form-control">
            </div>
            <div class="mb-3">
              <label for="productPrice" class="form-label">Product Price</label>
              <input type="text" name="price" class="form-control">
            </div>
            <div class="mb-3">
              <label for="productImage" class="form-label">Product Image</label>
              <input type="file" name="images" class="form-control" accept="image/jpg, image/jpeg, image/png">
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
          </form>
        </div>
        <div class="col-lg-12 mt-5">
          <div>
            <table class="table table-primary table-striped">
              <thead>
                <tr>
                  <th scope="col">No</th>
                  <th scope="col">Product Name</th>
                  <th scope="col">Product Price</th>
                  <th scope="col">Product Image</th>
                  <th scope="col">Status</th>
                  <th scope="col">Action</th>
                </tr>
              </thead>
              <tbody>
                <!-- @foreach ($products as $key => $product) -->
                <tr v-for="prod in prods">
                  <th scope="row">1</th>
                  <!-- <td>{{ $product->name }}</td> -->
                  <!-- <td>Rs.{{ $product->price }}</td> -->
                  <!-- <td><img src="{{ config('images.access_path') }}/{{ $product->images->name}}" alt="" class="table-img"></td> -->
                  <td>
                    <!-- @if ($product->status == 0)
                                    <span class="badge bg-warning">Not Active</span>
                                @else
                                <span class="badge bg-success">Active</span>
                                @endif -->
                  </td>
                  <td>
                    <!-- <a href="{{ route('product.delete', $product->id) }}" class="btn btn-danger"><i class="fa fa-trash"></i></a>
                                @if ($product->status == 0)
                                <a href="{{ route('product.status', $product->id) }}" class="btn btn-success"><i class="fa fa-check-circle"></i></a>
                                @else
                                <a href="{{ route('product.status', $product->id) }}" class="btn btn-warning"><i class="fa fa-check-circle"></i></a>
                                @endif -->
                  </td>
                </tr>
                <!-- @endforeach -->
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
  layout: 'dashboard',
  data() {
    return {
      tasks: [],
    }
  },

  methods: {
    getTasks() {
      this.$axios.get('http://localhost:3000/api/tasks').then(response => {
        console.log(response);
        this.tasks = response.data;
      });
    },
  },
  mounted() {
    this.getTasks();
  },
}
</script>

<style>
.page-title {
  padding-top: 5vh;
  font-size: 5rem;
  color: blue;
}
</style>
