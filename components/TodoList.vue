<template>
  <v-row>
    <v-col v-for="todo in allTodos" :key="todo.id.toString()" cols="12" sm="6" md="4">
      <Todo :todo="todo" />
    </v-col>
  </v-row>
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
