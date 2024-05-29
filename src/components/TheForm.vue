<template>
    <form @submit.prevent="SubmitForm">
        <!-- <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Books_HD_%288314929977%29.jpg/640px-Books_HD_%288314929977%29.jpg" alt="nothing"> -->
        <div class="form_control"  :class="{invalid: usernamevalidity === 'invalid'}">
            <label>Name</label>
            <input type="text" name="user-name" id="user-name" v-model.trim="username" @blur="validity"> 
            <p v-if="usernamevalidity === 'invalid'">please enter a valid name!!!</p>
        </div>
        <div class="form_control">
            <label for="age">Your Age(years)</label>
            <input type="number" id="age" name="age" v-model="age">
        </div>
        <div class="form_control">
            <label for="refer">How did you hear about us?</label>
            <select name="refer" id="refer" v-model="refer">
                <option value="google">Google</option>
                <option value="wom">Word of mouth</option>
                <option value="newspaper">newspaper</option>
            </select>
        </div>
        <div class="form_control">
            <h2>what are you interested in?</h2>
            <div>
                <input type="checkbox" name="interest" id="interest-news" value="News" v-model="interest">
                <label for="interest-news">News</label>

            </div>
            <div>
                <input type="checkbox" name="interest" id="interest-tutorials" value="tutorials" v-model="interest">
                <label for="interest-tutorials">Tutorials</label>
            </div>
            <div>
                <input type="checkbox" name="interest" id="interest-nothing" value="nothing" v-model="interest">
                <label for="interest-nothing">Nothing</label>
            </div>

        </div>
        <div class="form_control">
            <h2>How do you learn?</h2>
            <div>
                <input type="radio" name="how" id="how-video" value="video" v-model="how">
                <label for="how-video">video</label>
            </div>
            <div>
                <input type="radio" name="how" id="how-blogs" value="c=blog" v-model="how">
                <label for="how-blogs">Blog</label>

            </div>
            <div>
                <input type="radio" name="how" id="how-others" value="other" v-model="how">
                <label for="how-others">other</label>
            </div>
        </div>
        <div class="form_control">
            <rating-control></rating-control>
        </div>
        <div>
            <input type="checkbox" name="confirm" id="confirm" v-model="confirm">
            <label for="confirm">Agree for term and conditions?</label>
        </div>
        <div>
            <button>SAVE DATA</button>
        </div>
    </form>
</template>

<script>
import RatingControl from './RatingControl.vue';

export default {
    components:{
        RatingControl
    },
    data(){
        return{
            username:'',
            age : null,
            refer : 'wom',
            interest : [],
            how: null,
            confirm: false,
            usernamevalidity : 'pending'
        };
    },
    methods:{
        SubmitForm(){
            console.log('username : ' + this.username);
            this.username='';
            console.log('age: ' + this.age);
            this.age=null;
            console.log('refer : ' + this.refer);
            this.refer='wom';
            console.log('interest: ' + this.interest);
            console.log('how: ' + this.how);
            this.how=null;
            this.interest=[];
            console.log('confirm :' + this.confirm);
            this.confirm=false;

        },
        validity(){
            if(this.username === ''){
                this.usernamevalidity = 'invalid';
            }
            else{
                this.usernamevalidity = 'valid';
            }

        }
    }
}

</script>

<style scoped>
form{
    margin: 2rem auto;
    max-width: 50rem;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    padding: 2rem;
    background-image: url('https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/Books_HD_%288314929977%29.jpg/640px-Books_HD_%288314929977%29.jpg');
}

.form_control{
margin: 0.5rem 0 ;
border-color: #002350;
}

.form_control.invalid input {
    border-color: red;
}

.form_control.invalid label{
    color: red;
}

label {
    font-weight: bold;
}

h2{
    font-size: 1rem;
    margin: 0.5rem 0;
}
input,
select {
    display: block;
    width: 100%;
    font:inherit;
    margin-top: 0.5rem;
    border-radius: 12px;
}

select {
    width : auto;

}
input[type='checkbox'],
input[type='radio']{
    display: inline-block;
    width: auto;
    margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label{
font-weight: normal;
}

button{
    font: inherit;
    border: 1px solid #0076bb;
    background-color: #0076bb;
    color: white;
    cursor: pointer;
    padding: 0.75rem 2rem;
    border-radius: 30px;
}

button:hover,
button:active {
    border-color: #002350;
    background-color: #002350;
}

</style>