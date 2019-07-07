<template>
    <div>
        <div v-if='lessThanFive'> good</div>
        <div v-else class='red'> bad</div>
    </div>
</template>

<script>
export default {
    props:
        {lessThanFive: Boolean}
    }
</script>
<style>
 .red{
     color:red
 }
</style>

