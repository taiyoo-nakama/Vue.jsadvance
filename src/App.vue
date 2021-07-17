<template>
  <div>
    <label>
      <input type="radio" value="all" v-model="filter" />
      全て表示
    </label>
    <label>
      <input type="radio" value="active" v-model="filter" />
      未完了のみを表示
    </label>
    <label>
      <input type="radio" value="done" v-model="filter" />
      完了済みのみを表示
    </label>
    <TaskList v-bind:task-list="filteredTaskList" />
  </div>
</template>


<script>
import TaskList from '../src/components/TaskList.vue';
export default {
  data(){
    return{
      filter:"all",
      taskList:[
        {
          id:1,
          name:"牛乳を買う",
          done:false,
          labellds:[1,2],
        },
        {
          id:2,
          name:"Vue.jsの本を買う",
          done:true,
          labellds:[1,3],
        },
      ],
    };
  },
    components:{TaskList},
    computed:{
      filteredTaskList(){
        let filtered;
        if(this.filter === "all"){
          return this.taskList;
        }else if(this.filter === "active"){
          filtered = this.taskList.filter((task)=>{
            return !task.done;
          });
        }else if(this.filter === "done"){
          filtered = this.taskList.filter((task)=>{
            return task.done;
          });
        }
        return filtered;
      },
    },
  };
  
</script>

