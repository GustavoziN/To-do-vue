<template>
   <div id="header">
        <input id="input" type="text" v-model="inputTask" placeholder="what's your taks?">
        <button @click="addTask" id="button"> + </button>
        <div id="container"></div>
   </div>
</template>


<script>
    export default {
        name: 'Todo',
        data() {
            return {
                inputTask: ''
            }
        },
        methods: {
            addTask() {
                const container = document.querySelector('#container')   
                const div = document.createElement('div')
                div.classList.add('Task')

                const taskText = document.createElement('p')
                taskText.innerHTML = this.inputTask
                div.appendChild(taskText)

                const elementDelButton = document.createElement('button')
                elementDelButton.innerHTML = 'x'
                elementDelButton.id = 'clean'
                div.appendChild(elementDelButton)

                if(this.inputTask == '') {
                    alert('digite algo')
                } else {
                    this.inputTask = ''
                   
                    container.appendChild(div)
                    div.appendChild(elementDelButton)

                }

      
            },

             taskDel() {
                addEventListener('click', (e)=> {
                    if(e.target.id == 'clean') {
                        const contentTask = document.querySelector('.Task')
                        contentTask.remove()
                    }
                })
            },

           
        },
        mounted() {
            this.taskDel()
      
        }
    }
</script>


<style>
        *  {
            font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        }

        #header {
            text-transform: uppercase;
            width: 610px;
            text-align: center;
            border-radius: 10px;
            margin: auto;
    }

        #input {
            background-color: #D8D8D8;
            border: none;
            margin-right: 10px;
            margin-top: 10px;
            width: 400px;
            outline: none;
            height: 50px;
        }

      
        #button {
            background-color: #FFBF00;
            border: none;
            width: 40px;
            height: 50px;
        }

        .Task {
            display: flex;
            margin-top: 10px;
            margin-left: 2px;
            margin-right: 2px;
            width: 600px;
            background: #D8D8D8;
            justify-content: space-between;
            align-items: center;
        }

       
        #clean {
            border: none;
            background: none;
            padding: 10px;
        }

  
</style>