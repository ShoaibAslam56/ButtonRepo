<template>
    <div id="maidiv">
        <button
        :class="classes"
        :disabled="disabled || loading"
        @click="handleClick">
        <span v-if="loading">Loading.....</span>
            <span v-else><slot> {{ name }}</slot></span>
        </button>

        
        <div v-if="showSuccess" class="overlay">
            <div class="overlay-content">
                <h2>Successfully Login </h2>
                <button @click="closeOverlay">Done</button>
            </div>
        </div>
    </div>
</template>

<script>

export default {



    name:'useableButton' ,
    data(){
        return {
            loading:false ,
            showSuccess:false
        }
    } ,
    props:{
        name:{
            type:String,
            default:''
        },
        disabled:{
            type:Boolean,
            default:false
        },
        coustomClass:{
            type:String,
            default:''
        }
    },
    methods:{
        handleClick(event){
            if(!this.disabled && !this.loading ){
                this.loading = true ;
                setTimeout(() => {
                   this.loading = false ;
                   this.showSuccess = true
                }, 3000);
                this.$emit('click', event)
            }
        },
        closeOverlay(){
            this.showSuccess = false
        }
        
    },
    computed:{
        classes(){
            return [
                'button',
            this.coustomClass
            ]
        }
    }
}
</script>

<style scoped>
.maidiv{
    height: 100vh;
    background-color: black;
}
.overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(1, 0, 0, 0.6); 
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

.overlay-content {
    text-align: center;
    background:rgb(45, 214, 45);
    padding: 20px;
    border-radius: 10px;
    color: white;
}

.overlay-content button {
    margin-top: 10px;
    padding: 10px 20px;
    background: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.overlay-content button:hover {
    background: #218838;
}
.button{
    background: black;
    color: white;
    width: 150px;
    height: 50px;
    font-size: 22px;
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    border: 2px solid;
    border-radius: 40px;
    font-weight: 500;
}
</style>
