<template>
    <base-card><h2>Add Resource</h2>
    <form @submit.prevent>
        <div class="input">
            <input id="tittle" v-model="enteredTittle" type="text" placeholder=" ">
            <label for="tittle">Tittle</label>
        </div>
        <div class="input">
            <input id="description" v-model="enteredDescription" type="text" placeholder=" "><label for="description">Description</label></div>
        <div class="input">
            <input id="link" v-model="enteredLink" type="text" placeholder=" "><label for="link">URL</label></div>
        <div class="btn">
            <base-button @click="submitResource">Add Resource</base-button></div>
    </form></base-card>
    <Modal :tittle="'All fields are obligatory'" :desc="'Please check all inputs and re-send the form'" @close-modal="onCloseModal" v-if="error"/>
</template>

<script>
import Modal from '../UI/Modal.vue';
    export default{
        emits:['submit-resource'],
        inject:['addresource'],
        components:{Modal},
        data() {
            return {
                enteredTittle:'',
                enteredDescription:'',
                enteredLink:'',
                error:false
            }
        },

        methods: {
            submitResource(){
                if([this.enteredTittle,this.enteredDescription,this.enteredLink].includes('')){
                    this.error = true
                }
                else{
                    this.addresource(this.enteredTittle,this.enteredDescription,this.enteredLinks)
                    this.error = false
                }
            },

            onCloseModal(){
                this.error = false
            }
        },
    };
</script>

<style scoped>
    h2{
        text-align: center;
    }
    
    form{
        width: 100%;
        display: grid;
        grid-template-columns: 100%;
        place-items: center;
        gap: 25px;
    }


    .input{
        position: relative;
        width: 100%;
    }
    
    input{
        padding: 22px 10px 5px 10px;
        width: 100%;
        outline: none;
        border: none;
        border-bottom: 2px solid #3a0061;
        background-color:#a319ff14 ;
        font-size: 1em;
    }


    input:focus ~ label,
    input:not(:placeholder-shown) ~ label{
        font-size: 0.6em;
        transform: translateY(-8px);
    }

    .input label{
        position: absolute;
        left: 10px;
        top: 15px;
        transition: 0.1s;
        cursor: pointer;
    }

    
</style>