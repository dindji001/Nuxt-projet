<template>
  <main>
    <h1>TO-DO-LIST APP</h1>
    <p>Creer une liste de tache</p>

    <div class="create-new">
      <input
        type="text"
        v-model="newTask"
        placeholder="Ajouter une tache"
        @keypress.enter="addTask" />
      <button @click="addTask">Ajouter</button>
    </div>

    <div class="tasks">
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" />
    </div>

  </main>
</template>

<script>
export default {
  data (){
    return {
      newTask: ''
    }
  },
  methods: {
    addTask () {
      if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = '';
      }
    }
  }
}
</script>
