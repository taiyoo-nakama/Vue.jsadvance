<template>
  <div>
    <input type="text" v-model="filterWord" />
  <ul>
    <li v-for="task in filteredTaskList" v-bind:key="task.id">
      {{task.name}}
    </li>
    </ul>
  </div>
</template>


<script>
export default {
  name:"TaskList",
  props:{
    taskList:{
      type:Array,
      required:true,
    },
  },
  data(){
    return{
      filterWord:"",
    };
  },
  computed:{
    filteredTaskList(){
      const filtered = this.taskList.filter((taks) =>{
        return task.name.includes(this.filterWord);
      });
      return filtered;
    },
  },
};
</script>
