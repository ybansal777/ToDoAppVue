<script>
  export default {
    data() {
      return {
        tasks: [],
        newTask: "",
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() !== "") {
          this.tasks.push({ text: this.newTask, checked: false });
          this.newTask = "";
        }
      },
      deleteTask(index) {
        this.tasks.splice(index, 1);
      },
      moveTaskUp(index) {
        if (index > 0) {
          this.swapTasks(index, index - 1);
        }
      },
      moveTaskDown(index) {
        if (index < this.tasks.length - 1) {
          this.swapTasks(index, index + 1);
        }
      },
      swapTasks(index1, index2) {
        const temp = this.tasks[index1];
        this.tasks.splice(index1, 1, this.tasks[index2]);
        this.tasks.splice(index2, 1, temp);
      }
    }
  };
  </script>


<template>
    <div class="to-do-list">
      <h1>To-Do-List</h1>
  
      <div>
        <input
          type="text"
          placeholder="Enter a task..."
          v-model="newTask"
        />
        <button
          class="add-button"
          @click="addTask"
        >
          Add
        </button>
      </div>
  
      <ol>
        <li v-for="(task, index) in tasks" :key="index">
          <input
            type="checkbox"
            v-model="task.checked"
          />
          <span class="text">{{ task.text }}</span>
          <button
            class="delete-button"
            @click="deleteTask(index)"
          >
            Delete
          </button>
          <button
            class="move-button"
            @click="moveTaskUp(index)"
          >
            Move Up
          </button>
          <button
            class="move-button"
            @click="moveTaskDown(index)"
          >
            Move Down
          </button>
        </li>
      </ol>
    </div>
  </template>
  

  
  <style scoped>
  .to-do-list {
    font-family: Arial, sans-serif;
    text-align: center;
    margin-top: 100px;
  }

  h1 {
    font-size: 4rem;
    background-color: crimson;
    color: yellow;
    border-radius: 5px;
  }

  button {
    font-size: 1.7rem;
    font-weight: bold;
    padding: 10px 20px;
    color: Yellow;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.5s ease;
  }

  .add-button {
    background-color: crimson;
  }

  .add-button:hover {
    background-color: rgb(62, 4, 16);
  }

  .delete-button {
    background-color: crimson;
  }

  .delete-button:hover {
    background-color: rgb(62, 4, 16);
  }

  .move-button {
    background-color: crimson;
  }

  .move-button:hover {
    background-color: rgb(62, 4, 16);
  }

  input[type="text"] {
    font-size: 1.6rem;
    padding: 10px;
    border: 2px solid black;
    border-radius: 5px;
    color: black;
  }

  input[type="checkbox"] {
    padding: 8px 12px;
    width: 1.4rem;
    height: 1.4rem;
    accent-color: crimson;
  }

  ol {
    padding: 0;
  }

  li {
    font-size: 2rem;
    font-weight: bold;
    padding: 15px;
    background-color: white;
    margin-bottom: 10px;
    border: 3px solid lightgrey;
    border-radius: 5px;
    display: flex;
    align-items: center;
  }

  .text {
    flex: 1;
  }

  .delete-button, .move-button {
    padding: 8px 12px;
    font-size: 1.4rem;
    margin-left: 10px;
  }
  </style>
  