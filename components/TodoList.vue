<template>
  <v-list>
    <v-list-item v-for="todo in allTodos" :key="todo.id.toString()">
      <Todo :todo="todo" />
    </v-list-item>
  </v-list>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { namespace } from 'vuex-class'
import Todo from '~/components/Todo.vue'
import * as todos from '~/store/modules/todos'

const Todos = namespace(todos.name)

@Component({
  components: {
    Todo,
  },
})
export default class TodoList extends Vue {
  @Todos.Getter allTodos?: any
}
</script>
