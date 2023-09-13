<template>
  <v-card>
    <v-card-title style="font-size: 24px;"> เข้าสู่ระบบ </v-card-title>
    <v-card-text>

      <v-form
      ref="loginFrom"
      v-model="valid"
      lazy-validation
      >
    
      <v-text-field
      v-model="username"
      :counter="50"
      :rules="nameRules"
      label="Username" 
      required
      outlined
      ></v-text-field>
      
      <v-text-field
      v-model="password"
      :rules="passwordRules"
      :type="show1 ? 'text' : 'password'"
      label="Password"
      required
      outlined
      ></v-text-field>
      
      <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4"
      @click="Login()"
      block
      >
      เข้าสู่ระบบ
    </v-btn>
    
</v-form>
</v-card-text>
</v-card>
</template>
<script>
export default {
  data: () => ({
    valid: true,
    username: '',
    nameRules: [
      v => !!v || 'กรุณากรอกชื่อผู้ใช้งาน', 
      v => (v && v.length <= 50) || 'กรุณากรอกชื่อไม่เกินจำนวน 50 ตัวอักษร',
    ],
    password: '',
    passwordRules: [
      v => !!v || 'กรุณากรอกรหัสผ่าน',
    ]
    
  }),

  methods: {
    Login () {
      if(this.$refs.loginFrom.validate(true)){
      localStorage.setItem('username',this.username)
      this.$EventBus.$emit('getUsername')
      this.$router.push("/")
      } 
    },
  },
}
</script>

<style>
</style>