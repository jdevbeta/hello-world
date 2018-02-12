<template>
  <div>
    <button v-on:click="active.component = 'sqblRegister'">
        <icon name="user" dims="20,20"></icon>
        <span>New User?</span>
    </button>
    <div>
      <form @submit.prevent="submitUserForm" ref="form">
        <h1>Sign In</h1>
        <label> Username: </label>
        <input 
          type="text" 
          pattern="[a-zA-Z0-9]+" 
          id="inputUser" 
          v-model="system.user.display" 
          title="Use Letters A - Z and Numbers 0 - 9."
        />
        <label> Password: </label>
        <input 
          type="password"
          id="inputPass"
          pattern="(?=.*\d)(?=.*[a-zA-Z]).{4,}"
          title="Password must have a Number and a Letter. Minimum of 4 Characters."
        />
        <input type="submit" value="Submit" />
      </form>
    </div>
  </div>
</template>

<script>
import sqblIcons from './icons.vue'

export default {
  name: 'sqblLogin',
  props: ['system', 'active'],
  methods: {
    submitUserForm(){
      var formEl = this.$refs.form;
      var formArray = formEl.getElementsByTagName('input');
      for(var i=0; i<formArray.length; i++){
        if(formArray[i].value == "" || typeof formArray[i].value !== "string"){
          console.log('Focused on'+formArray[i].previousElementSibling.innerHTML+formArray[i].value)
          return formArray[i].focus()
        }
      }
      console.log("Success! Submit Form Now.");
    }
  },
  components: {
    'icon': sqblIcons
  
  },
  data () {
    return {
      
    }
  }
}
</script>

<style scoped>
  button {
    display: inline-block;
    position: relative;
    margin: 0;
    padding: 5px 5px 2px 5px;
    font-family: 'Roboto Condensed';
    font-size: 20px;
    text-align: center;
    color: #333;
  }

  button span {
    margin-right: 5px;
  }

  div {
    display: block;
    margin: auto;
    text-align: center;
    font-family: 'Roboto Condensed';
  }
  
  label {
    display: block;
    font-size: 18px;
  }
  
  input {
    display: inline-block;
    margin-bottom: 4px;
    width: 100%;
    box-sizing: border-box;
    padding: 5px 10px;
    text-align: center;
  }

  input[type="submit"]{
    width: 50%;
    margin-top: 20px;
  }

  form {
    display: block;
    margin: auto;
    margin-top: 20px;
    padding: 10px;
    padding-top: 20px;
    width: 50%;
    min-width: 250px;
    border: 1px solid #333;
  }

  h1 {
    margin: 0;
    padding: 0;
    text-align: left;
    color: #555;
  }

</style>
