<template>
    <div>
        <ul>
            <li v-bind:class="{updating: item.id === updateInfo.item.id, ['list-item']: true}" v-bind:key="item.id" v-for="(item, index) in toDoList"> 
                <div>Item: {{item.task}}</div>
                <div>Priority: {{item.priority}}</div>
                <div>
                    <span v-on:click='deleteItem(index)'>x</span>
                    <span v-on:click='setToUpdate(item)'> update</span>
                </div>
            </li>

        </ul>
        <BusyWarning v-bind:lessThanFive='lessThanFive'/>

        <UpdateTodo v-if='updateInfo.item.id' @update-done='clearForm' v-bind:item ="updateInfo.item" v-bind:index="updateInfo.index"/>
        <NewToDo v-else  @submit-new-to-do='addNewToDo'/> 
    </div>
</template>

<script>

import NewToDo from './NewToDo'
import UpdateTodo from './UpdateTodo'
import BusyWarning from './BusyWarning'
export default {
    data(){
        return {
            toDoList: [{task: "buy pears", priority: "low", id: window.updateGlobalId()}, {task: "get shit together", priority: "high", id: window.updateGlobalId()}],
            updateInfo: {
                item: {},
                index: -1
            }
        }
    },
    methods: {
        addNewToDo(data){
            this.toDoList.push(data)
            
        }, 
        deleteItem(index){
            this.toDoList.splice(index, 1)
            this.clearForm()
        }, 
        setToUpdate(item){
            this.updateInfo.item  = item;
        },
        clearForm(){
            this.updateInfo.item  = {}
        }
    },
    computed: {
        lessThanFive(){
            return this.toDoList.length < 5
        }
    },
    components: {
        NewToDo, UpdateTodo, BusyWarning
    },
    watch :{
        toDoList(){
            this.$emit('length-update', this.toDoList.length)
        }
    }
}
</script>

<style>
    .list-item{
        margin: 20px;
    }
    .updating{
        font-weight: bold
    }
</style>

