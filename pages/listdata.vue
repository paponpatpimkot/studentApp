<template>
  <div class="container mt-5 w-50">
    <button class="btn btn-primary mb-3" @click="addStudent">AddStudent</button>
    <table class="table table-striped">
      <thead class="table-dark">
        <tr>
          <th>No.</th>
          <th>ID</th>
          <th>CODE</th>
          <th>NAME</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(student,idx) in students" :key="student.id">
          <td>{{idx+1}}</td>
          <td>{{student.id}}</td>
          <td>{{student.code}}</td>
          <td>{{student.name}}</td>
          <td>
            <button class="btn btn-danger me-3" @click="delStudent(student)"><i class="bi bi-trash3"></i></button>
            <button class="btn btn-success" @click="editStudent(student)"><i class="bi bi-pencil"></i></button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
  export default {
    data(){
      let students = []
      for(let i = 1;i<=10;i++){
        students.push({
          id:100+i,
          code:String(i).padStart(4,'0'),
          name:`Student${i}`
        })
      }
      return {
        students
      }
    },
    methods:{
      addStudent(){
        let id=100+this.students.length+1
        this.students.push({
          id,
          code:String(id-100).padStart(4,'0'),
          name:`Student${id-100}`
        })
      },
      delStudent(std){
        let idx=this.students.findIndex(x=> x.id === std.id)
        this.students.splice(idx,1)
      },
      editStudent(std){
        this.$router.push(`/student/${std.code}`)
      }
    }
  }

</script>