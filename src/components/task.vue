<template>
    <div class="container">
        <div class="bg-light rounded p-5">
            <h1 class="text-center mb-5">To Do</h1>
            <div class="mt-3 mb-5 d-flex justify-content-evenly">
                <input type="text" class="form-control mr-3" placeholder="Enter your work" v-model="input" >
                <input type="time" class="form-control mr-3" placeholder="" v-model="inputTime">
                <input type="date" class="form-control" placeholder="" v-model="inputDate" >
                <i class="far fa-plus-square plus pl-2" @click="addClick"></i>
            </div>

            <div class="message px-1" >
                <table>  
                    <TaskItem 
                        v-bind:todo="todo"
                        v-for="(todo, index) in todos"
                        :key="todo.id"
                        @remove="removeTask(index)"
                        @complete="completeTask(todo)">
                    </TaskItem>
                </table>
            </div>

            <div class="d-flex justify-content-between mb-5 buttons">
                <button class="" @click="clearCompleted">Clear completed</button>
                <button class="" @click="clearAll">Clear all</button>
            </div>

            <div class="px-1">
                <span>pending tasks: {{incomplete}}</span>
            </div>
        </div>
    </div>
</template>

<script>
import TaskItem from './taskItem'

export default {  
    name:"Todo",
    props: ['todos'],
    components:{
        TaskItem
        },
    data(){
        return{
            input: '',
            inputDate: '',
            inputTime: ''
        }
    },
    computed:{
          incomplete() {
            return this.todos.filter(this.inProgress).length;
        },
    },
    mounted:function(){
            let d1 = this.inputDate.split('-').concat(this.inputTime.split(':')).map(Number)
            if(new Date(d1[0],d1[1]-1,d1[2],d1[3],d1[4]) === new Date()){
                console.log(true)
            }else if(new Date(d1[0],d1[1]-1,d1[2],d1[3],d1[4]) === new Date()){
                console.log(false)          
            }
        },
    methods:{
        addClick(){
            console.log(this.inputTime)
            console.log(this.inputDate)
           
            if(this.input && this.inputDate && this.inputTime){
                this.todos.push({
                    title: this.input,
                    time: this.inputTime,
                    date: this.inputDate,
                    completed: false
                })
                this.input = ''
                this.inputTime = ''
                this.inputDate = ''
            }
           
           
            // console.log(new Date(d1[0],d1[1]-1,d1[2],d1[3],d1[4]))
            // console.log(new Date())
                                             
                    // }else if(new Date(d1[0],d1[1]-1,d1[2],d1[3],d1[4]) !== new Date()){
                    //     console.log('not Equal')
                    // }
                
        },
        inProgress(todo){                
            return !this.isCompleted(todo)
        },
        isCompleted(todo) {
            return todo.completed;
        },
        clearCompleted(){
                if(confirm('you want to delete completed the task?')){
                this.todos = this.todos.filter(this.inProgress);
                }
        },
        clearAll(){
            if((this.todos.length>0)){
                if(confirm('you want to delete all the task')){
                    this.todos = []
                }
            }else{
                alert('there is nothing to clear')
            }
        },
        completeTask(todo){
           todo.completed = !todo.completed
        },
        removeTask(index){
            if(confirm('you want to delete?')){
            this.todos.splice(index, 1)
            }
        }
    }
}

</script>
 