<template>
    <div>
        <h1 class="display-4 text-center">Listado de Tareas</h1>
        <hr>
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <div class="card mt-4">
                    <div class="card-body">
                        <div class="input-group">
                           <input type="text" v-model="tareita" class="form-control form-control-lg" placeholder="Agregar tarea">
                        <div class="input-group-append">
                            <button v-on:click="agregarTarea()" class="btn btn-success btn-lg">
                                Agregar
                            </button>
                        </div>
                </div>
                <br>
              
                <ul class="list-group">
                    <li v-for="(MyTarea,index) of listTareas" :key="index" 
                        class="list-group-item d-flex justify-content-between">
                        <span class="material-symbols-outlined cursor">
                            circle
                        </span>
                        {{MyTarea.nombre}}
                        <span class="material-symbols-outlined text-danger cursor">
                            delete
                        </span>
                    </li>
                 </ul>
            </div>
        </div>
      </div>  
   </div>
</div>
</template>

<script>
    export default {
        name: 'MyTarea',
        data(){
            return{
                tareita:"",
                listTareas:[]
            } 
      },
      methods:{
        agregarTarea(){
            const tareita = {
                nombre:this.tareita,
                estado: false
            }
            this.listTareas.push(tareita);
            this.tareita = "";
        }
      }
  }
</script>

<style scoped>
    .cursor{
        cursor:pointer
    }
</style>