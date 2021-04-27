<template>
    <div class="contain d-flex flex-column justify-content-center align-item-center">
        <div class="border border-secondary p-3 content">
            <h1>TODO</h1>
            <div class="input-group mt-3">
                <input type="text" class="form-control" placeholder="Enter your work" v-model="input">
                <div class="input-group-append" v-if="!isEditing">
                    <i class="far fa-plus-square plus pl-2" @click="addClick"></i>
                </div>

                <div class="input-group-append" v-else>
                    <i class="far fa-plus-square plus pl-2" @click="updateMessage"></i>
                </div>


            </div>
            <div class="border border-secondary message mt-4 p-3 d-block" >
                <div >
                    <ol >
                        <li v-for="(todo,index) in todos" :key="todo" class="bg-light text-left m-2 p-3 rounded h5">
                            {{todo}}
                            <i class="far fa-edit text-primary" @click="editMessage(index,todo)"></i>
                            <i class="fas fa-times text-danger" @click="removeMessage(index)"></i>    
                        </li>
                        
                    </ol>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {  
    data(){
        return{
            input: '',
            selectedIndex:'',
            isEditing: false,
            todos: [],
        }
    },
    methods: {
        addClick(e){
            if(this.input === ''){
                e.preventDefault()
            }else{
                this.todos.push(this.input)
                this.input = ''
            }
        },
        editMessage(index,todo){
            this.selectedIndex = index
            this.input = todo
            this.isEditing = true
        },
        updateMessage(){
            this.todos.splice(this.selectedIndex1,1,this.input)
            this.input = ''
            this.isEditing = false
        },
        removeMessage(index){
            console.log(index)
            this.todos.splice(index, 1)
        }
    }
}
</script>

<style scoped>
    @media screen and (min-width: 762px) {
        .content{
        background-color: rgb(164, 27, 177);
        height: 45rem !important;
        width: 48rem !important;
        }
        .message{
            height: 30rem !important;
        }
    }
    @media screen and (min-width: 960px){
        .contain{
            margin-left: 28rem;
        }
        .content{
        background-color: rgb(164, 27, 177);
        height: 35rem !important;
        width: 30rem !important;
        }
        .message{
            height: 25rem !important;
        }
    }
   
    .plus{
        color: white;
        font-size: 2.55rem;
    }
    .content{
        background-color: rgb(164, 27, 177);
        height: 25rem;
        width: 13.5rem;
    }
    .message{
        background-color: rgb(113, 51, 119);
        height: 15rem;
        overflow-x: auto;
    }
    ::-webkit-scrollbar {
        width: 0; /* Remove scrollbar space */
        background: transparent; /* Optional: just make scrollbar invisible */
    }
</style>
