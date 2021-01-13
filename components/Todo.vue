<template>
  <v-card>
    <v-card-text>
      <v-text-field
        v-show="todo.isEditing"
        :id="todo.id.toString()"
        type="text"
        filled
        rounded
        :value="todo.content"
        @keyup.enter="updateTodo"
      />
      <v-text-field
        v-show="!todo.isEditing"
        :id="todo.id.toString()"
        disabled
        type="text"
        filled
        rounded
        :value="todo.content"
        @keyup.enter="updateTodo"
      />
    </v-card-text>
    <v-card-actions>
      <v-btn
        v-show="!todo.isEditing"
        class="button is-info"
        @click="editTodo(todo.id.toString())"
      >
        Edit
      </v-btn>
      <v-btn
        v-show="todo.isEditing"
        class="button is-info"
        disabled
        @click="editTodo(todo.id.toString())"
      >
        Edit
      </v-btn>
      <v-btn @click="removeTodo(todo.id.toString())">DONE</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import { namespace } from 'vuex-class'
import * as todos from '~/store/modules/todos'

const Todos = namespace(todos.name)

@Component
export default class Todo extends Vue {
  @Prop() todo?: any
  @Todos.Action removeTodo?: void
  @Todos.Action editTodo?: void
  @Todos.Action updateTodo?: void
}
</script>
