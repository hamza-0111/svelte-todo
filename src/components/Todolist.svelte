<script>
    let newTodo = '';  
    let todos = [];  
  
    function addTodo() {
      if (newTodo.trim()) {
        todos = [...todos, { text: newTodo, id: Date.now(), done: false }];
        newTodo = '';  
      }
    }
  
    function remove(id) {
      todos = todos.filter(todo => todo.id !== id);
    }
  
    function Done(id) {
      todos = todos.map(todo => 
        todo.id === id ? { ...todo, done: true } : todo
      );
    }
</script>


<div>
  <h1>To-Do List</h1>

  <input type="text" bind:value={newTodo} placeholder="Add new to-do" />
  <button on:click={addTodo}>Add</button>

  <div class="list-container">
    <div class="list-title">Pending Tasks</div>
    <ul class="todo-list">
      {#each todos.filter(todo => !todo.done) as todo (todo.id)}
        <li class="todo-item">
          <span>{todo.text}</span>
          <button class="button" on:click={() => Done(todo.id)}>Mark as Done</button>
          <button class="button" on:click={() => remove(todo.id)}>Remove</button>
        </li>
      {/each}
    </ul>
  </div>

  <div class="list-container">
    <div class="list-title">Completed Tasks</div>
    <ul class="todo-list">
      {#each todos.filter(todo => todo.done) as todo (todo.id)}
        <li class="todo-item done">
          <span>{todo.text}</span>
          <button class="button" on:click={() => remove(todo.id)}>Remove</button>
        </li>
      {/each}
    </ul>
  </div>
</div>



<style>
    div {
      max-width: 500px;
      margin: 50px auto;
      padding: 20px;
      background-color: #f9f9f9;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
      text-align: center;
    }
  
    h1 {
      color: #4CAF50;
      font-size: 2rem;
      margin-bottom: 20px;
    }
  
    input {
      padding: 10px;
      font-size: 16px;
      width: 75%;
      border: 2px solid #ddd;
      border-radius: 4px;
      outline: none;
      transition: border-color 0.3s;
    }
  
    input:focus {
      border-color: #4CAF50;
    }
  
    button {
      padding: 10px 15px;
      font-size: 16px;
      margin-left: 10px;
      background-color: #4CAF50;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
  
    button:hover {
      background-color: #45a049;
    }
  
    .todo-list {
      list-style-type: none;
      padding: 0;
      margin-top: 20px;
    }
  
    .todo-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 12px;
      margin: 6px 0;
      background-color: #fff;
      border-radius: 6px;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
  
    .todo-item:hover {
      transform: translateY(-3px);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    }
  
    .todo-item.done {
      background-color: #e0ffe0;
      color: #6b6b6b;
      text-decoration: line-through;
    }
  
    .todo-item span {
      flex-grow: 1; 
    }
  
    .button {
      background-color: #f44336;
      color: white;
      border: none;
      padding: 5px 10px;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
  
    .button:hover {
      background-color: #d32f2f;
    }
  
    .list-container {
      margin-top: 40px;
    }
  
    .list-title {
      font-size: 1.5rem;
      font-weight: bold;
      color: #333;
      margin-bottom: 10px;
      text-align: left;
    }
  
    ul {
      padding-left: 10px;
    }
  </style>