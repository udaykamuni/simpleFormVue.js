<template>       
    <ul>
        <li :class="{active : activeOption === 'poor'}">
            <button type="button" @click="activate('poor')">poor</button>
        </li>
        <li :class="{active : activeOption === 'Average'}">
            <button type="button" @click="activate('Average')">Average</button>
        </li>
        <li :class="{active : activeOption === 'great'}">
            <button type="button" @click="activate('great')">Great</button>
        </li>
    </ul>
</template>

<script>
export default {
    data(){
        return {
            activeOption: null
        };
    },
    methods:{
        activate(option){
            this.activeOption = option;
        }
    }
}
</script>

<style scoped>
.active{
    border-color: rgb(255, 0, 0);
    border: red;
}
.active button {
    color: red;
}

ul{
    list-style: none;
    margin : 0.5rem 0;
    padding: 1rem;
    display: flex;
    justify-content: center;
    align-items: center;
}
li{
    margin: 0 1rem;
    border: 1px soild #ccc;
    display: flex;
    padding-left: 2rem;
    justify-content: cemter;
    align-items: center;
}

button{
    font : inherit;
    border: 2px;
    background-color: transparent;
    cursor: pointer;
    border-color: black;
    padding: 2px;
    margin: auto;
}

button:hover {
    color: rgb(0, 255, 55);
}
</style>