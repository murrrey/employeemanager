<template>
<div id='new-employee'>
<h3>New Employee</h3>
  <form @submit.prevent="saveEmployee" class="col s12">
    <div class="row">
    <div class="input-field col s12">
      <input type="text" v-model ="employee_id"
      required>
      <label>Employee ID#</label>
    </div></div>
 <div class="row">
    <div class="input-field col s12">
      <input type="text" v-model ="name"
      required>
      <label>Name</label>
    </div></div>
     <div class="row">
    <div class="input-field col s12">
      <input type="text" v-model ="dept"
      required>
      <label>Department</label>
    </div></div>
     <div class="row">
    <div class="input-field col s12">
      <input type="text" v-model ="position"
      required>
      <label>Position</label>
    </div></div>
    <button type="submit" class="btn">submit</button>
    <router-link to="/" class="btn grey">cancel</router-link>
    </form>
</div>
</template>

<script>
import db from './firebaseinit'
import { error } from 'util'
export default {

    name: 'new-employee',
    data(){    

      return{
         employee_id:null,
          name: null,
          dept: null,
          position:null

      }
    },

    methods: {
     saveEmployee () {
       db.collection('employees').add({
         employee_id: this.employee_id,
         name: this.name,
         dept:this.dept,
         position:this.position
       })
       .then(docRef =>{
         this.$router.push('/dashboard')
         .catch(error => console.log(err))
       })
     }

    }
}
</script>