<template>
<div>
    <h3>{{headerText}}</h3>
    <b>count: {{length}} </b>
    </div>
</template>
<script>
export default {
    data: ()=>({
        headerText: "Vue to-do, a big todo"
    }),
    props: {
        length: Number
        }
}
</script>
