<template>
  <!-- Start Header -->
  <header
    class="p-2 bg-pcolor text-3xl text-tcolor font-black shadow-sm w-full"
  >
    <div
      class="flex justify-center items-center md:justify-start lg:justify-start"
    >
      <svg
        class="ml-4 opacity-25"
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
  <!-- Start 1st Face -->
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
  <form
    class="flex justify-start text-3xl md:text-5xl lg:text-5xl p-2"
    @submit.prevent="addNewTodo"
  >
    <input
      v-model="todoTitle"
      class="p-3 ml-4"
      type="text"
      placeholder="Type here e.g. buy bacon"
    />
  </form>
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
    v-for="todo in allTodos"
    :key="todo.id"
    class="
      main-div
      bg-gray-50
      flex
      justify-between
      items-center
      p-4
      mt-2
      border-t-2 border-b-2
      hover:border-gray-30
    "
    :class="todo.td_status == 't' ? 'line-through' : 'no-underline'"
  >
    <div class="flex justify-start items-center">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-6 w-6"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
        id="iconL"
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
        class="w-7 h-7 border-green-700 ml-2 cursor-pointer"
        @click="onclick(todo)"
      />

      <div class="addtodo">
        <input
          type="text"
          id="title"
          :value="todo.td_title"
          onblur="getVal()"
        />
        <input type="text" id="description" :value="todo.td_body" />
        <input type="text" id="description" :value="todo.td_status" />
      </div>

      <div class="td-text">
        <button
          class="text-xs ml-3 bg-gray-200 rounded p-1 text-gray-500"
          @click="calender"
          id="date"
        >
          No due date
        </button>
      </div>
    </div>

    <div class="flex justify-end" id="iconsR">
      <!-- side icons -->
      <div class="relative z-0 group">
        <button type="button" class="group-hover:text-blue-500">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 mx-5 cursor-pointer"
            viewBox="0 0 20 20"
            fill="currentColor"
            strokeColor="currentColor"
          >
            <path
              d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"
            />
          </svg>
        </button>
        <div
          class="
            absolute
            -top-8
            bg-opacity-0
            text-opacity-0
            w-25
            z-10
            h-6
            text-gray-100 text-capitalize
            bg-black
            group-hover:bg-opacity-100 group-hover:text-opacity-100
          "
        >
          Star task
        </div>
      </div>
      <div class="relative z-0 group">
        <button type="button" class="group-hover:text-yellow-500">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 mx-2 cursor-pointer"
            viewBox="0 0 20 20"
            fill="currentColor"
            strokeColor="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M17.707 9.293a1 1 0 010 1.414l-7 7a1 1 0 01-1.414 0l-7-7A.997.997 0 012 10V5a3 3 0 013-3h5c.256 0 .512.098.707.293l7 7zM5 6a1 1 0 100-2 1 1 0 000 2z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
        <div
          class="
            absolute
            -top-8
            -left-10
            bg-opacity-0
            text-opacity-0
            w-72
            z-10
            h-6
            text-gray-100 text-capitalize
            bg-black
            group-hover:bg-opacity-100 group-hover:text-opacity-100
          "
        >
          Tag task with color
        </div>
      </div>
      <div class="relative z-0 group">
        <button
          type="button"
          class="group-hover:text-red-500"
          @click="deleteTodo(todo)"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 mx-5 cursor-pointer"
            viewBox="0 0 20 20"
            fill="currentColor"
            strokeColor="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
        <div
          class="
            absolute
            -top-8
            bg-opacity-0
            text-opacity-0
            w-15
            h-6
            text-gray-100 text-capitalize
            bg-black
            group-hover:bg-opacity-100 group-hover:text-opacity-100
          "
        >
          Delete task
        </div>
      </div>
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

  <div class="todoButton">
    <button @click="posttodo">AddNewTodo</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      allTodos: [],
      post: [],
      put: [],
      currentId: null,
      todosId: [],
      todo: [],
      doneTodos: [],
      todoTitle: "",
      addHyphen: true,
    };
  },

  mounted() {
    this.getAllTodos();
  },

  methods: {
    async getAllTodos() {
      await axios
        .get("https://safitodos.000webhostapp.com/api/todos/get/all")
        .then((response) => {
          console.log(response);
          this.allTodos = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    getTodoById(id) {
      axios
        .get(`https://safitodos.000webhostapp.com/api/todos/get/${id}`)
        .then((response) => {
          console.log(response.data);
          this.todosId = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    postTodo() {
      axios
        .post("https://safitodos.000webhostapp.com/api/todos/add", {
          td_title: "todo 1",
          td_body: "paragraph for todo 1",
          td_status: "f",
        })
        .then((response) => {
          console.log(response);
          this.post = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    updateTodo() {
      axios
        .post(
          `https://safitodos.000webhostapp.com/api/todos/update/${this.currentId}`,
          {
            td_title: "todo 1",
            td_body: "paragraph for todo 1",
            td_status: "f",
          }
        )
        .then((response) => {
          console.log(response);
          this.post = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    addNewTodo() {
      axios.post("https://safitodos.000webhostapp.com/api/todos/add", {
        td_title: this.todoTitle,
        td_body: "paragraph for todo 1",
        td_status: "f",
      });
      console.log(this.todoTitle);
    },

    onclick(todoItem) {
      if (todoItem.td_status == "t") {
        todoItem.td_status = "f";
        console.log("unchecked");
      } else {
        todoItem.td_status = "t";
        console.log("checked");
      }
    },

    deleteTodo(todo) {
      this.allTodos.splice(this.allTodos.indexOf(todo), 1);
      console.log("delete");
    },
  },
  computed: {
    AllTODOSItems() {
      return this.allTodos.length;
    },
  },
};
</script>

<style>
.addtodo {
  margin-top: 5px;
  padding: 10px 60px;
  align-items: center;
}
.addtodo input {
  display: block;
  background: none;
}
.addtodo input:focus {
  border: 1px solid black;
  outline-width: 0 !important;
}
.addtodo input[type="text"]:focus {
  width: fit-content;
  background-color: violet;
  color: white !important;
}

.addtodo input:first-child {
  font-size: 30px;
  font-weight: bold;
  text-transform: uppercase;
}
address input:nth-child(2) {
  font-size: 25px;
  color: rgb(34, 31, 32);
  font-style: italic;
}

.addtodo input:last-child {
  font-size: 20px;
  color: rgb(34, 31, 32);
  font-style: italic;
}

.todoButton button {
  background: rgb(110, 47, 141);
  border: 0;
  padding: 10px 20px;
  color: white;
  margin-top: 20px;
  border-radius: 20px;
  cursor: pointer;
}
</style>
