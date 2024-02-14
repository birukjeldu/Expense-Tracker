<template>
    <div>
        <h1>{{ income }}  Income || {{ expense }} - Expense</h1>
        
    </div>
</template>

<script>

export default{
    props: ['expense','income']
}
</script>