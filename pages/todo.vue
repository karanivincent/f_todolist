<template>
  <div class="h-screen bg-gray-200 w-screen">
    <div class=" grid grid-cols-4 gap-4 px-4">
      <div class="col-span-4 row-auto sm:col-span-2 p-2 ">
        <h3 class=" text-xl font-semibold text-gray-800">
          TODOS
        </h3>
        <div class=" rounded overflow-hidden">
          <form class="mb-3 flex" @submit.prevent="addTodo">
            <input v-model="newTodo" type="text" required class=" flex-1 px-2 py-1 rounded border text-gray-700 focus:border-gray-500 focus:outline-none ">
            <button type="submit" class=" mx-2 bg-orange-600 px-6 py-1 inline-block rounded text-white uppercase">
              <h3 class=" text-xl font-semibold">
                Add
              </h3>
            </button>
          </form>
          <draggable
            v-model="todos"
            class="divide-y divide-orange-200"
            animation="500"
            ghost-class="todo-ghost-class"
            group="todos"

            @change="log"
          >
            <div
              v-for="(element, i) in todos"
              :key="i"
              class=" bg-white   py-1 px-2 cursor-move text-orange-600"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-span-4 row-auto sm:col-span-2 p-2">
        <h3 class=" text-xl font-semibold text-gray-800">
          COMPLETED
        </h3>
        <div class="rounded overflow-hidden">
          <draggable
            v-model="completed"
            class=" divide-y divide-lime-300"
            animation="500"
            ghost-class="blue-background-class"
            group="todos"
            @change="log"
          >
            <div
              v-for="element in completed"
              :key="element.name"
              class=" bg-white  py-1 px-2 cursor-move text-green-700"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import draggable from 'vuedraggable'

export default {
  name: 'TwoLists',
  display: 'Two Lists',
  order: 1,
  components: {
    draggable
  },
  data () {
    return {
      newTodo: '',
      todos: [
        { name: 'John', id: 1 },
        { name: 'Joao', id: 2 },
        { name: 'Jean', id: 3 },
        { name: 'Gerard', id: 4 }
      ],
      completed: [
        { name: 'Juan', id: 5 },
        { name: 'Edgard', id: 6 },
        { name: 'Johnson', id: 7 }
      ]
    }
  },
  methods: {
    addTodo () {
      this.todos.push({ name: this.newTodo })
    },
    replace () {
      this.list = [{ name: 'Edgard' }]
    },
    clone (el) {
      return {
        name: el.name + ' cloned'
      }
    },
    log (evt) {
      console.log('LIST ONE')
      this.todos.forEach((element) => {
        console.log(element.name)
      })
      console.log('LIST TWO')

      this.completed.forEach((element) => {
        console.log(element.name)
      })

      window.console.log(evt)
    }
  }
}
</script>

<style>
.todo-ghost-class {
  @apply bg-orange-200;
}
.blue-background-class {
  background: #dcedc1;
}

</style>
