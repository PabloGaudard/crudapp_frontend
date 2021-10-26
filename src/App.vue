<template>
  <div id="app" class="mt-5">
    <div class="container">
      <div class="row">
        <div class="col-2">
          <button type="button" class="btn btn-success w-100">
            Add Record
          </button>
        </div>
        <div class="col">
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              aria-label="Text input with dropdown button"
              placeholder="Search"
            />
            <button
              class="btn btn-outline-secondary dropdown-toggle"
              type="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
            >
              Filter
            </button>
            <ul class="dropdown-menu dropdown-menu-end">
              <li><a class="dropdown-item" href="#">First Name</a></li>
              <li><a class="dropdown-item" href="#">Last Name</a></li>
              <li><a class="dropdown-item" href="#">Role</a></li>
              <li><a class="dropdown-item" href="#">Country</a></li>
            </ul>
          </div>
        </div>
        <div class="col-2">
          <button type="button" class="btn btn-success w-100">Search</button>
        </div>
      </div>
      <div class="row">
        <table class="table">
          <thead class="thead-light">
            <tr>
              <th scope="col">ID</th>
              <th scope="col">First Name</th>
              <th scope="col">Last Name</th>
              <th scope="col">Role</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(person, i) in people" :key="i">
              <th scope="row">1</th>
              <td>{{ person.firstname }}</td>
              <td>{{ person.lastname }}</td>
              <td>{{ person.role }}</td>
              <td>
                <button type="button" class="btn btn-warning">Edit</button>
              </td>
              <td>
                <button type="button" class="btn btn-danger">Delete</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="row">
        <nav aria-label="Page navigation example">
          <ul class="pagination">
            <li class="page-item">
              <a class="page-link" href="#">Previous</a>
            </li>
            <li class="page-item"><a class="page-link" href="#">1</a></li>
            <li class="page-item"><a class="page-link" href="#">2</a></li>
            <li class="page-item"><a class="page-link" href="#">3</a></li>
            <li class="page-item"><a class="page-link" href="#">Next</a></li>
          </ul>
        </nav>
      </div>
    </div>

    <div class="container mt-5 mb-5">
      <div class="row">
        <div class="col-2">
          <button type="button" class="btn btn-success w-100">
            Save
          </button>
        </div>
        <div class="col-2">
          <button type="button" class="btn btn-success w-100">
            Cancel
          </button>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <form>
            <div class="form-group row">
              <label for="inputEmail3" class="col-sm-2 col-form-label"
                >ID</label
              >
              <div class="col-sm-10">
                <input class="form-control" />
              </div>
            </div>
            <div class="form-group row">
              <label class="col-sm-2 col-form-label"
                >First Name</label
              >
              <div class="col-sm-10">
                <input class="form-control" />
              </div>
            </div>
            <div class="form-group row">
              <label class="col-sm-2 col-form-label"
                >Last Name</label
              >
              <div class="col-sm-10">
                <input class="form-control" />
              </div>
            </div>

            <div class="form-group row">
              <div class="col-sm-2">Active</div>
              <div class="col-sm-10">
                <div class="form-check">
                  <input
                    class="form-check-input"
                    type="checkbox"
                    id="gridCheck1"
                    checked
                  />
                </div>
              </div>
            </div>

            <div class="form-group row">
              <label class="col-sm-2 col-form-label"
                >Role</label
              >
              <div class="col-sm-10">
                <input class="form-control" />
              </div>
            </div>

            <div class="form-group row">
              <label class="col-sm-2 col-form-label"
                >Country</label
              >
              <div class="col-sm-10">
                <input class="form-control" />
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.col-sm-10{
  padding-top: 10px;
}
</style>

<script>
export default {
  data() {
    return {
      people: [
        {
          firstname: "Andrew",
          lastname: "Smith",
          role: "dev",
          country: "Brazil",
        },
        {
          firstname: "John",
          lastname: "Adams",
          role: "admin",
          country: "Mexico",
        },
      ],
    };
  },
  created() {
    var oReq = new XMLHttpRequest();
    oReq.onload = () => {
      console.log(this.responseText);
    };
    oReq.open("get", "http://localhost:5000/list", true);
    oReq.send();
  },
};
</script>
