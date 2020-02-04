<template>
<div>

  <div class="container mt-4">
      <h1><img src="favicon.ico" alt="">CRUD Operation Using Vue JS</h1>
      <hr>
  </div>
<div class="container">          
            <div class="row">
                <div  class="col-md-6">
                    <table class="table border">
                        <thead>
                          <tr>
                            <th scope="col">id</th>
                            <th scope="col">name</th>
                            <th scope="col">role</th>
                            <th scope="col">Action</th>
                            
                          </tr>
                        </thead>
                        <tbody>
                          <tr v-for="(person,index) in persons" :key="index">  
                            <th scope="row">{{parseInt(index) + 1}}</th>
                            <td>{{person.name}}</td>
                            <td>{{person.role}}</td>
                            <td>
                                <button class="btn btn-danger" @click="removeItem(index)">Delete</button>
                                <button class="btn btn-info" @click="updateItem(person)">Edit</button>
                               
                            </td>                            
                          </tr>                                                    
                        </tbody>
                      </table>
                </div>
                <div class="col-md-6">
                    <div class="card shadow p-4">
                        <h2 class="mb-4">Please Add New Users</h2>
                        <p>your name is {{user.name}} and your role is {{user.role}}</p>

                        <form @submit.prevent = "addUser">
                            <div class="form-group">
                                <label>Name</label>
                                <input v-model="user.name" type="text"  class="form-control">    
                            </div>

                            <div class="form-group">
                                <label>Role</label>
                                <input v-model="user.role" type="text"  class="form-control">    
                            </div>

                            <div class="form-group">
                                <button v-if="status" type="submit" class="btn btn-primary">Submit</button>                                            
                                <button v-else  type="click" @click.prevent="updatePerson" class="btn btn-info ml-5">Update</button>
                                <button type="reset" class="btn btn-danger" @click="back">Reset</button>
                            </div>

                        </form>
    
    
                    </div>
                    

                </div>
            </div>
        </div>
        <div class="container mt-4">

          <h6 style="text-align: center">&copy;Kemzyyoung Tony  Project Create</h6>

        </div>
</div>
</template>

<script>
import swal from 'sweetalert';
export default {
    data(){
        return{
            status: true,
      message: "Hello Vue",
      persons: [
            {name: "wisdom", role: "Html dev" },
            {name: "Ekemini", role: "JS dev" },
            {name: "Mercy", role: "php dev" },
            {name: "Daniel", role: "UI/UX dev" },
            {name: "Mata", role: "UX dev" } 
       ],
        
        user : 
          {
              name : "",
              role : "",
        },
        
        }
    },

    methods: {
      addUser(){
        
        this.persons.push(this.user)
        swal("Welcome!", "You are now a member!", "success");
        
      },
      
      removeItem(index) {        
       
      swal({
            title: "Are you sure?",
            text: "Once deleted, you will not be able to recover this imaginary file!",
            icon: "warning",
            buttons: true,
            dangerMode: true,
            })
            .then((willDelete) => {
            if (willDelete) {
              this.persons.splice(index, 1); 
            swal("Poof! Your imaginary file has been deleted!", {
              icon: "success",
            });
            } else {
            swal("Your imaginary file is safe!");
            }
      });

        // alert("Delete me");
      },
      updateItem(id){
        // console.log(id);
        // this.user.name = id.name;
        // this.user.role = id.role;

        this.status = !this.status;
        this.user = id;
      },
      updatePerson() {
        alert('hello');
      },
      back(){
        this.status = !this.status; 	
      }


      


    
        }
    
        
    }
</script>