<template>
    <form v-if="item.id" @submit.prevent='onSubmit'>
        <input type="text" v-model='item.task' placeholder='update task'>
        <select v-model='item.priority' name="priorities" >
            <option value="low">Low</option>
            <option value="medium">medium</option>
            <option value="high">high</option>

        </select>
        <input type="submit" value='done'> 

    </form>
</template>
<script>
export default {
    
    props: {
        item: Object, index: Number
    },
    methods: {
        onSubmit(){
            this.$emit('update-done')
        }
    }
}
</script>
