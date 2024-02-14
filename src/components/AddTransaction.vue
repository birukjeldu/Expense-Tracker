<template>
    <div>
        <form @submit.prevent="addTransaction" class="p-4">
            <label for="">Title:</label><br>
            <input type="text" v-model="title" name="" id=""><br><br>
            <label for="">Amount:</label><br>
            <input type="number" v-model="amount" name="" id="" ><br>
            <button>Submit</button><br>
        </form>

        
    </div>
</template>

<script>
import { ref, defineEmits } from 'vue';

export default {
  props: ['transaction'],
  setup(props, { emit }) {
    const title = ref('');
    const amount = ref(0);

    function generateRandomUniqueID() {
    const usedIDs = new Set();

    while (true) {
        const randomID = Math.floor(Math.random() * 100) + 1; // Generate a random number between 1 and 100

        if (!usedIDs.has(randomID)) {
            usedIDs.add(randomID);
            return randomID;
        }
    }
}

    

const addTransaction = () => {
    const transactionData = {
        id: generateRandomUniqueID(),
        titel: title.value,
        value: amount.value
    };

    emit('transactionSubmitted', transactionData);
    
    title.value = '';
    amount.value = 0;
};

    return { title, amount, addTransaction };
  }
};
</script>