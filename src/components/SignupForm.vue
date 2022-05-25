<template>
  <form @submit.prevent="handleSubmit">
    <div>
      <label>Email:</label>

      <input required type="email" v-model="email">
    </div>

    <div>
      <label>Password:</label>

      <input required type="password" v-model="password">

      <div class="error" v-if="passwordError">
        {{ passwordError }}
      </div>
    </div>

    <div>
      <label>Role:</label>

      <select v-model="role">
        <option value="Developer">Web Developer</option>
        <option value="Designer">Web Designer</option>
      </select>
    </div>

    <div>
      <label>Skills:</label>

      <input type="text" @keyup.alt="addSkill" v-model="tempSkill">

      <div class="pill" :key="skill" v-for="skill in skills">
        <span @click="removeSkill(skill)">{{ skill }}</span>
      </div>
    </div>

    <div class="terms">
      <input required type="checkbox" v-model="terms">

      <label>Accept Terms and Conditions</label>
    </div>
    
    <div class="submit">
      <button>Create an Account</button>
    </div>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        role: '',
        terms: false,
        tempSkill: '',
        skills: [],
        passwordError: ''
      }
    },

    methods: {
      addSkill(e) {
        if (e.key === ',' && this.tempSkill) {
          if (!this.skills.includes(this.tempSkill)) {
            this.skills.push(this.tempSkill)
          }

          this.tempSkill = ''
        }
      },

      removeSkill(e) {
        this.skills = this.skills.filter((item) => {
          return e !== item
        })
      },

      handleSubmit() {
        this.passwordError = this.password.length > 5 ? '' : 'Password must be at least 6 characters long.'

        if (!this.passwordError) {
          console.log('Email: ', this.email)
          console.log('Password: ', this.password)
          console.log('Role: ', this.role)
          console.log('Skills: ', this.skills)
          console.log('Terms Accepted: ', this.terms)
        }
      }
    }
  }
</script>

<style scoped>
  button {
    background: #0b6dff;
    border-radius: 20px;
    border: 0;
    color: #fff;
    margin-top: 20px;
    padding: 10px 20px;
  }

  form {
    background: #fff;
    border-radius: 10px;
    margin: 30px auto;
    max-width: 420px;
    padding: 40px;
    text-align: left;
  }

  input, select {
    border: none;
    border-bottom: 1px solid #ddd;
    box-sizing: border-box;
    color: #555;
    display: block;
    padding: 10px 6px;
    width: 100%;
  }

  input[type="checkbox"] {
    display: inline-block;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
    width: 16px;
  }

  label {
    color: #aaa;
    display: inline-block;
    font-size: 0.6em;
    font-weight: bold;
    letter-spacing: 1px;
    margin: 25px 0 15px;
    text-transform: uppercase;
  }

  .pill {
    background-color: #eee;
    border-radius: 20px;
    color: #777;
    cursor: pointer;
    display: inline-block;
    font-size: 12px;
    font-weight: bold;
    letter-spacing: 1px;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
  }

  .submit {
    text-align: center;
  }

  .error {
    color: #ff0062;
    font-size: 0.8em;
    font-weight: bold;
    margin-top: 10px;
  }
</style>