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
                            <button v-on:click="agregarTarea()" class="btn btn-success btn-lg">Agregar</button>
                        </div>
                </div>

                <br>

                <h5 v-if="listTareas.length ==0">No hay tareas para realizar</h5>
              
                <ul class="list-group">
                    <li v-for="(MyTarea,index) of listTareas" :key="index" class="list-group-item d-flex justify-content-between">
                        <span class="cursor" v-bind:class="{'text-success': MyTarea.estado}"
                        v-on:click="editarTarea(MyTarea, index)">
                            <i v-bind:class="[MyTarea.estado ? 'fa-solid fa-circle-check' : 'far fa-circle']"></i>
                       </span>
                          {{MyTarea.nombre}}
                        <span class="text-danger cursor" v-on:click="eliminarTarea(index)">
                            <i class="fas fa-trash-alt"></i>
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
        },

        eliminarTarea(index){
            this.listTareas.splice(index, 1)
        },
        editarTarea(MyTarea, index){
            this.listTareas[index].estado =  !MyTarea.estado
        }
    }
}
</script>

<style scoped>
    .cursor{
        cursor:pointer
    }
</style>