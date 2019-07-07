<template>
    <form @submit.prevent='onSubmit'>
        <input type="text" v-model='itemText' placeholder='new task'>
        <select v-model='itemPriority' name="priorities" >
            <option value="low">Low</option>
            <option value="medium">medium</option>
            <option value="high">high</option>

        </select>
        <input type="submit">

    </form>
</template>
<script>
export default {
    data: ()=>(
        {
            itemText: '',
            itemPriority: 'low'
        }
    ),
    methods:{
        onSubmit(){
            const {itemText, itemPriority} = this
            this.$emit('submit-new-to-do',
                {task: itemText, priority:itemPriority, id: window.updateGlobalId()}
            )
            this.itemText = '';
            this.itemPriority = 'low'
            
        }
    }
}
</script>

