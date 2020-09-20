<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username"/>
    </div>
    <div>
      <label for="password">password: </label>
      <input id="password" type="password" v-model="password"/>
    </div>
    <button type="submit">login</button>
  </form>
    
</template>

<script>
import axios from 'axios';

export default {
  data: function(){
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    submitForm: function() {
      //Form은 기본설정상 submit가 클릭되면 새로고침을 하는데, 이래서는 이벤트설정및 로직이 초기화 되어버린다.
      //event.preventDefault()를 이용해 기본설정 이벤트(새로고침)을 막자.
      //그러나 vue에서는 v-on:submit.prevent를 이용해 이걸 간단히 해결할수 있다.
      //event.preventDefault()
      console.log(this.username, this.password);
      var url='https://jsonplaceholder.typicode.com/users';
      var data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
        .then(function(response){
          console.log(response);
        })
        .catch(function(error){
          console.log(error);
        });
    }
  }

}
</script>

<style>

</style>