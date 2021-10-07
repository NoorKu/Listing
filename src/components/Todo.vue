<template>
  <!-- Start Header -->
  <header
    class="p-2 bg-pcolor text-3xl text-tcolor font-black shadow-sm w-full"
  >
    <div
      class="flex justify-center items-center md:justify-start lg:justify-start"
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
      flex
      justify-start
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
  <div
  
   class="flex justify-start text-3xl md:text-5xl lg:text-5xl p-2" >
    <input 
      class="p-3 ml-4" 
      type="text"
      placeholder="Type here e.g. buy bacon"
     
    />
  </div>
  <div
    class="
      rounded
      bg-gray-800
      text-white
      p-1
      ml-10
      hidden
      md:inline-block
      lg:inline-block
    "
  >
  
    <h3>Enter your first task and press enter to save</h3>
  </div>
   <!-- End 1st Face -->
  <!-- Start 2nd Face -->
  <div
    class="
      bg-gray-50
      flex
      justify-between
      items-center
      p-4
      mt-2
      border-t-2 border-b-2
      hover:border-gray-300
    "

  >
    <div class="flex justify-start items-center hiddenN">
      <!-- side icons -->
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-6 w-6"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M3 4h13M3 8h9m-9 4h9m5-4v12m0 0l-4-4m4 4l4-4"
        />
      </svg>
      <input
        type="checkbox"
        id="vehicle1"
        name="vehicle1"
        value="Bike"
        class="w-7 h-7 border-green-700 ml-2"
      />
      <p class="text-xs ml-3 bg-gray-200 rounded p-1 text-gray-500">
        No due date
      </p>
    </div>
    <div class="flex justify-end">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-5 w-5 mx-5"
        viewBox="0 0 20 20"
        fill="currentColor"
      >
        <path
          d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"
        />
      </svg>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-5 w-5 mx-2"
        viewBox="0 0 20 20"
        fill="currentColor"
      >
        <path
          fill-rule="evenodd"
          d="M17.707 9.293a1 1 0 010 1.414l-7 7a1 1 0 01-1.414 0l-7-7A.997.997 0 012 10V5a3 3 0 013-3h5c.256 0 .512.098.707.293l7 7zM5 6a1 1 0 100-2 1 1 0 000 2z"
          clip-rule="evenodd"
        />
      </svg>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-5 w-5 mx-5"
        viewBox="0 0 20 20"
        fill="currentColor"
      >
        <path
          fill-rule="evenodd"
          d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
          clip-rule="evenodd"
        />
      </svg>
    </div>
  </div>

  <!-- End 2nd Face -->

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

<div class="add">
    <button @click="addnewtodos">AddNewTodo</button>
</div>


  <h1>AllTODOS: {{ AllTODOSItems }}</h1>
  <div v-for="adding in allTodos" :key="adding" class="adding">
    <p>allTodos: {{ adding.td_title }} {{ adding.td_body }} {{ adding.td_status }}</p>
    <div id="td">
      <p>Td_title: {{ adding.td_title}}</p>
  <p>Td-body: {{ adding.td_body }}</p>
  <p>Td-status: {{ adding.td_status }}</p>
    </div>
  </div>
</template>

<script>
const axios = require('axios');
export default {
 
  
 data() {
    return {
      allTodos: [],
      post: [],
      put: [],
      currentId: -1,
      todosId: [],
      show: false,
      addnew: [],
	
    
     
    }
       
      
    },
  
  mounted() {
    console.log('page loaded')
    console.log('all todos', this.allTodos)
    this.getAllTodos()

    console.log('tododId')
    this.addtodosId()

    console.log('post')
    this.addpost()

    console.log('post')
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

        console.log(error)
      })
    },

    addtodosId() {
      axios.get(`https://safitodos.000webhostapp.com/api/todos/get/${currentId}`)
      .then(response => {
        console.log(response);
        this.todosId = response.data
      })
      .catch(error => {
        console.log(error)
      })

    },
    
    addpost(){
      axios.post('https://safitodos.000webhostapp.com/api/todos/add',{
	"td_title":"todo 1",
	"td_body":"paragraph for todo 1",
	"td_status":"f"
})
      .then(response => {
        console.log(response);
        this.post = response.data
      })
      .catch(error =>{
        console.log(error);
      })
    },

    updateput() {
      axios.post(`https://safitodos.000webhostapp.com/api/todos/update/${currentId}`,{
	"td_title":"todo 1",
	"td_body":"paragraph for todo 1",
	"td_status":"f"
})
      .then(response => {
        console.log(response);
        this.post = response.data
      })
      .catch(error =>{
        console.log(error)
      })
    },

    deletetodos() {
      axios.post(`https://safitodos.000webhostapp.com/api/todos/delete/${currentId}`)
      .then(response => {
        console.log(response)
        this.post = response.data
      })
      .catch(error => {
        console.log(error)
      })
    },

   addnewtodos() {
   console.log("click")
 axios.post('https://safitodos.000webhostapp.com/api/todos/add',{
	td_title:"todo 1",
	td_body:"paragraph for todo 1",
	td_status:"f"
})
 .then(response => {
        console.log('add success',response)
        this.addnew = response.data
      })
      .catch(error => {
        console.log('add error', error)
      })


},
   
  },
  computed: {
      AllTODOSItems() {
        return this.allTodos.length
      },
     
  }


}
</script>

<style>
.adding {
  margin-top: 5px;
  font-size: 20px;
  font-style: italic;
  padding: 10px 15px;
}
.adding p:first-child {
  font-weight: bold;
  font-style: normal;
}
.adding #td p:first-child{
  font-weight: normal;
  font-style: italic;
}
.adding #td p {
  background-color: gray;
  color: black
}

.add button {
  background-color: rebeccapurple;
  color: white;
  border: 0;
  padding: 10px 15px;
  margin: 5px ;
  border-radius: 20px;
  cursor: pointer;
}



</style>