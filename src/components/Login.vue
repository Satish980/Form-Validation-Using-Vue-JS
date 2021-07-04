<template>
  <div>
    <form @submit="login">
    <input type="text" placeholder="enter name" v-model="name" ><br>
    <span class="text" ></span>
    <br>
    <input type="password" placeholder="enter passwrod" v-model="password"><br><br>
    <button type="submit">Login</button>
    </form>
    <p v-if="error.length">
        <b>Errors:</b>
        <ul>
            <li v-for="e in error" v-bind:key="e.id">
                {{e}}
            </li>
        </ul>
    </p>
  </div>
</template>
<script>
export default {
  name: 'Login',
  data () {
    return {
      error: [],
      name: null,
      password: null
    }
  },
  methods: {
    login (e) {
      if(this.name && this.password)
        console.log("Login Function Called")
      this.error = []
      if(!this.name)
        this.error.push("name is required")
      if(!this.password)
        this.error.push("password is required")
    console.warn("errors " + this.error)
      e.preventDefault()
    }
  }
}
</script>
