<template>
    <teleport to='#app'>
    <div class="modal">
        <div class="modal-container">
            <h2>{{ tittle }}</h2>
            <p>{{ desc }}</p>
            <div class="btn">
                <base-button @click="closeModal">Close</base-button>
            </div>
        </div>
    </div>
    </teleport>
</template>

<script>
    export default{
        emits:['close-modal'],
        props:['tittle','desc'],
        methods: {
            closeModal(){
                this.$emit('close-modal')
            }
        },
    };
</script>

<style scoped>
    .modal{
        position: fixed;
        top:0;
        left: 0;
        right: 0;
        width: 100vw;
        height: 100vh;
        background-color: rgba(0, 0, 0, 0.4);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .btn{
        width: fit-content;
        margin: auto;
    }

    .modal-container{
        background-color: white;
        padding: 0;
        width:70%;
        border-radius: 10px;
        padding-bottom: 20px;
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

    h2{
        margin: 0;
        background-color: #3a0061;
        color: white;
        padding: 10px;
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
    }

    p{
        padding-left: 10px;
    }


</style>