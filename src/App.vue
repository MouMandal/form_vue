<script setup>
import { ref, computed } from 'vue';
const data = ref({
    firstName: "",
    lastName: "",
    username: "",
    email: "",
    address: "",
});
//computed property
const isFormValid = computed(() => {
    return (
        data.value.firstName && data.value.lastName && data.value.userName && data.value.email && data.value.address
    )
})
//create a function for submit button
const submit = () => {
    if (isFormValid.value) {
        console.warn("form is submitted", data.value);
    }
    else {
        console.warn("try to check it please");
    }
}
</script>
<template>
    <div class="container">
        <form @submit.prevent="submit">
            <h1>Form Validation Using Vue.js</h1>
            <div class="first">
                <div class="input1">
                    <p>First name</p>
                    <input type="text" v-model="data.firstName">
                </div>
                <div class="input2">
                    <p>Last name</p>
                    <input type="text" v-model="data.lastName">
                </div>
            </div>
            <div class="second">
                <p>Username</p>
                <input type="text" placeholder="username" v-model="data.userName">
                <p>Email</p>
                <input type="text" placeholder="Enter your email" v-model="data.email">
                <p>Address</p>
                <input type="text" placeholder="Enter your address" v-model="data.address">
            </div>
            <button type="submit" :disabled="!isFormValid" class="submit-button">Submit</button>
        </form>
    </div>
</template>