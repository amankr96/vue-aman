<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>User Name: {{ myName }} </p>
        <p>User Age: {{ userAge }} </p>
        <button @click="resetName">Reset Name</button>
    </div>
</template>

<script>
import { eventBus} from '../main';
export default {
    props: {
        myName: {
            type: String
        },
        userAge:{
            type: Number 
        } 
    },
    methods: {
        resetName() {
            this.myName='Max';
            this.$emit('nameWasReset',this.myName);
        }
    },
        created()
        {
            eventBus.$on('ageWasEdited', (age) => {
                this.userAge=age;
            }); 
        }
}
</script>

<style scoped>
    div {
        background-color: rgb(128, 240, 193);
    }
</style>
