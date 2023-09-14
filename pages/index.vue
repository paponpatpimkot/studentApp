<template>
  <div class="container">
    <p>ID : {{  id }}</p>
    <p>Name : {{  name }}</p>
    <p>Major : {{ major }}</p>
    <p>Username : {{ username }}</p>
    <p>Password : {{ password }}</p>
    <p>
      แก้ไขรหัสผ่าน 
      <input type="text" v-model="password">
      <button>Save</button>
    </p>
  </div>
</template>
<script>
  export default {
    data(){
      return{
        id: '66309010001',
        name: 'นายกฤษณะพงศ์',
        username: '66309010001@tatc.ac.th',
        password: '123456789'
      }
    }
  }
</script>