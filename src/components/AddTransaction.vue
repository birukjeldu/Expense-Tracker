<template>
    <div>
        <form action="" class="p-4">
            <label for="">Title:</label><br>
            <input type="text" v-model="title" name="" id=""><br><br>
            <label for="">Amount:</label><br>
            <input type="number" v-model="amount" name="" id="" ><br>
        </form>
        <button @submit="addTransaction" class="">Submit</button><br>
    </div>
</template>

<script>
import  {ref} from 'vue'
 export default{
    props: ['transaction'],
    setup(props){
        const title = ref('')
        const amount = ref('')

        console.log(props.transaction)

        const addTransaction = ()=>{
            props.transaction.push({title:title,value:amount})
        }
        return {title, amount}
    }
 }
</script>