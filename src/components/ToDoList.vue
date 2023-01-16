<template>
  <div>
    <div>
      <input
        type="text"
        @change="inputValue = $event.target.value"
        :value="inputValue"
        class="formInput"
        placeholder="Task..."
      />
      <button @click="addTask(inputValue)" class="formButton">Add</button>
    </div>

    <div>
      <p v-for="task in allTasks" @click="removeTask(task)" class="taskText">
        {{ task }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  data() {
    return {
      inputValue: "",
      allTasks: []
    };
  },
  methods: {
    addTask(taskName) {
      if (taskName.length > 0) {
        this.allTasks.push(taskName);
        this.inputValue = "";
      }
    },
    removeTask(taskName) {
      const itemIndex = this.allTasks.findIndex(i => i === taskName);
      this.allTasks.splice(itemIndex, 1);
    }
  }
};
</script>

<style scoped>
.formInput {
  width: 200px;
  border: 1px solid #ddd;
  font-family: inherit;
  padding: 10px 10px;
  border-radius: 4px;
}

.formButton {
  font-family: inherit;
  border: 0;
  background-color: #243763;
  color: #fff;
  padding: 10px 16px;
  border-radius: 4px;
  cursor: pointer;
}

.taskText {
  cursor: pointer;
  margin: 10px 0;
}

.taskText::before {
  content: "-";
  margin-left: 10px;
}
</style>
