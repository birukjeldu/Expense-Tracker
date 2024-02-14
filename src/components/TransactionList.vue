<template>
    <div class="m-5">
        <h2>Transaction History</h2>
        <div v-for="items in transaction" :key="items.id">
            <li :class="{ 'm-1 p-2 border-r-4': true, 'border-green-500': items.value>0,'border-red-500':items.value<0 }">{{ items.value }}  - {{ items.titel }}  </li>
        </div>
        
    </div>
</template>

<script>

export default{
    props: ['transaction'],
    setup(){

    }
}
</script>