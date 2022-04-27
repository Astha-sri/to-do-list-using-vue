<template>
  <div class="container">
    <h2 class="text-center mt-5">My todo-list</h2>
  
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter Task to do" class="form-control">
      <button @click="addTask" class="btn btn btn-primary">ADD</button>
    </div>
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col" class="text-center">Edit</th>
          <th scope="col" class="text-center">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>{{task.name}}</td>
          <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen pointer" ></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
               <span class="fa fa-trash pointer"></span>
            </div>
          </td>
   
        </tr>
 
      </tbody>
    </table>
  </div>  
  
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

data(){
  return{
    task:'',
    editedTask:null,
    tasks:[]
  }
},
methods: {
  addTask(){
    if(this.task.length === 0) return 0;
    if (this.editedTask===null){
    this.tasks.push({
      name:this.task
    });
    }else{
      this.tasks[this.editedTask].name=this.task;
      this.editedTask=null;
    }
    this.task=''
  },
  deleteTask(index){
    this.tasks.splice(index,1);
  },
  editTask(index){
    this.task=this.tasks[index].name;
    this.editedTask=index
  }
}
};
</script>


<style scoped>

</style>
