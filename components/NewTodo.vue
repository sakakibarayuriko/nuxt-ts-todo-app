<template>
  <v-row>
    <v-col cols="12" sm="6" md="4">
      <v-text-field
        placeholder="Write new TODO..."
        type="text"
        filled
        rounded
        @keydown.enter="addTodo"
      />
    </v-col>
  </v-row>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator'
import { Action, namespace } from 'vuex-class'
import * as todos from '~/store/modules/todos'
const Todos = namespace(todos.name)

@Component
export default class NewTodo extends Vue {
  @Todos.Action addTodo?: void
}
</script>
