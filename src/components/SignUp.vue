<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type = "email" required v-model="email">
    <label>Password:</label>
    <input type = "password" required v-model="password">
    <label>Role</label>
    <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
    </select>
    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill">
    <div v-for="el in skills" :key="el">
        <span @click="deleteSkill(el)">{{el}}</span>
    </div>
    <label>Accept T&C</label>
    <input type="checkbox" required v-model="terms">
    <button >Create an Acc.</button>
  </form>
  <p>Email value::{{email}}</p>
  <p>password::{{password}}</p>
  <p>role::{{role}}</p>
  <p>terms::{{terms}}</p>
  <p>SKILLS::{{skills}}</p>
</template>

<script>
export default {
data(){
    return {
        email: '',
        password:'',
        role:'designer',
        terms:'',
        tempSkill:'',
        skills : []
    }
},
methods:{
    addSkill(e){
     //   console.log(e)
     if(e.key==='Enter' && this.tempSkill){
        if(!this.skills.includes(this.tempSkill)){
         this.skills.push(this.tempSkill)
        }
        this.tempSkill=''
     }
    },
    deleteSkill(el){
        this.skills=this.skills.filter(item=> item !== el)
    },
    handleSubmit(){
        console.log('form submitted')
    },
    submit(e){
        console.log(e)
        e.preventDefault()

    }
}

}
</script>

<style>

</style>