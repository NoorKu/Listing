<template>
  <!-- Start Header -->
    <header class="p-2 bg-pcolor text-3xl text-tcolor font-black shadow-sm">
      <div
        class="
          flex
          justify-center
          items-center
          md:justify-start
          lg:justify-start
        "
      >
        <svg
          class="ml-4"
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
        >
          <path
            d="M19 0h-14c-2.762 0-5 2.239-5 5v14c0 2.761 2.238 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-8.959 17l-4.5-4.319 1.395-1.435 3.08 2.937 7.021-7.183 1.422 1.409-8.418 8.591z"
          />
        </svg>
        <h2 class="pl-1">flask</h2>
      </div>
    </header>
    <!-- End Header -->

    <!-- Start Container -->
    <div
      class="
        text-2xl
        md:text-3xl
        lg:text-3xl
        bg-gray-200
        p-3
        text-gray-800
        shadow-sm
      "
    >
      <h2 class="ml-4">Create your to-do list below</h2>
    </div>
    <div class="text-3xl md:text-5xl lg:text-5xl p-2">
      <input
        class="p-3 ml-4"
        type="text"
        placeholder="Type here e.g. buy bacon"
      />
    </div>
    <div
      class="
        bg-gray-900
        text-white
        p-1
        ml-10
        hidden
        md:inline-block
        lg:inline-block
      "
    >
      <h3 id="cs">Enter your first task and press enter to save</h3>
    </div>

    <!-- End Container -->

    <!-- Start Footer -->
    <footer class="fixed inset-x-0 bottom-0 p-4">
      <div class="flex justify-end items-end m-4">
        <input
          class="p-2 bg-gcolor text-white font-bold rounded shadow-md"
          type="button"
          value="Buy Me A Coffee"
        />
      </div>
    </footer>
    <h1> AllTODOS: {{ AllTODOSItems }} </h1>
</template>

<script>
const axios = require('axios');
export default {
 data() {
    return {
      allTodos: [],
      post: [],
      put: []
    }
  },
  mounted() {
    console.log('page loaded')
    console.log('all todos', this.allTodos)
    this.getAllTodos()

    console.log('post')
    this.addpost()

    console.log('put')
    this.updateput()

  },
  methods: {
    getAllTodos() {
    axios.get('https://safitodos.000webhostapp.com/api/todos/get/all')
      .then(response => {
        console.log(response);
        this.allTodos = response.data
      })
      .catch(error => {

        console.log(error);
      })
    },
    addtodos(){
      axios.post('https://safitodos.000webhostapp.com/api/todos/add')
      .then(response => {
        console.log(response);
        this.post = response.data
      })
      .catch(error =>{
        console.log(error);
      })
    },
    updateput() {
      axios.put('https://safitodos.000webhostapp.com/api/todos/update/{id}')
      .then(response => {
        console.log(response);
        this.put = response.data
      })
      .catch(error =>{
        console.log(error)
      })
    },
    deletetodos() {
      axios.delete('https://safitodos.000webhostapp.com/api/todos/delete/{id')
      .then(response => {
        console.log(response)
      })
      .catch(error => {
        console.log(error)
      })
    }
  },
  computed: {
      AllTODOSItems() {
        return this.allTodos.length
      }
    },


}
</script>

<style>

</style>