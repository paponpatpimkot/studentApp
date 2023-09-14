<template>
  <div class="container w-50" style="margin-top:150px">
    <div class="card shadow p-3 mb-5 bg-body-tertiary rounded">
      <div class="card-body">
        <div class="mb-3">
          <label class="form-label">Username</label>
          <input type="text" ref="user" class="form-control" v-model="user" autofocus>
        </div>
        <div class="mb-3">
          <label for="password" class="form-label">Password</label>
          <input type="password" ref="pass" class="form-control" v-model="pass">
        </div>
        <button type="button" class="btn btn-primary me-2" :disabled="isLocked" @click="doLogin">Sing-In</button>
        <button type="button" class="btn btn-danger" @click="doReset">Reset</button>
      </div>
      <div class="text-danger text-center">{{ message }}</div>
    </div>
  </div>
</template>
<script>
  import axios from 'axios'
  export default {
    data() {
      return {
        user: '',
        pass: '',
        message: '',
      }
    },
    computed: {
      isLocked() {
        return this.user.length=== 0 || this.pass.length===0
      }
    },
    methods: {
      doLogin(){
        this.message = ''
        if(this.user === 'user' && this.pass === '1234'){
            this.$router.push('/listData')
        }else{
          this.message = 'user or pass incorrect'
          this.$refs.pass.focus()
        }
      },//doLogin
      doReset(){
        this.user = '',
        this.pass = '',
        this.message = '',
        this.$refs.user.focus()
      }
    }
  }
</script>