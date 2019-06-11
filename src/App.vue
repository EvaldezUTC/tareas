<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>

<template>



<div class="container">

    
        <div id= "taskApp" class="col-sm-8 col-sm-offset-2">
                <h1>{{nameApp}}</h1>
                <form v-on:submit="agregarTarea">
                    <input type="text" v-model= "tareas.titulo" class="form-control">
                    <input type="submit" value="Agregar Tarea" class=" btn btn-block btn btn-success" >
                </form>
                <br>
        
                <table class="table">
                    <thead>
                        <tr>
                            <th>Hecho!</th>
                            <th>Tatera</th>
                            <th>Eliminar</th>
                        </tr>
                    </thead>
                    
                    <tbody>
                        <tr -for = "tarea in Tareas">
                            <td>
                                <input type="checkbox" v-model="tarea.hecho">
                            </td>
                            <td :class= "{tareaRealizada: tarea.hecho}">
                                
                                {{tarea.titulo}} 
                            </td>
                            <td>
                                <button v-on:click="eliminarTarea(tarea)" class="btn btn-danger">
                                    Eliminar
                                </button>
                            </td>
                        </tr>
                    </tbody>
                </table>
        
            </div>
        
        
</div>



</template>

<script>

 new Vue ({
        el:'#taskApp',
        data: {
            nameApp: 'Tareas Vue.js',
            tareas: [
                {
                    titulo: 'tarea 1', 
                    hecho: true
                },
                {
                    titulo: 'tarea 2',
                    hecho: false 
                },
                {
                    titulo: 'tarea 3',
                    hecho: false 
                },
                 

            ]
        },
        methods: {
            eliminarTarea: function (tarea){
                 this.tareas.splice(this.tareas.indexOf(tarea), 1)
                console.log(this.tareas.indexOf(tarea));
            },
            agregarTarea: function (e){
                e.preventDefault();
                this.tareas.push({
                    titulo: this.tareas.titulo,
                    hecho: false
                });
                this.tareas.titulo = '';
                console.log(e);
            }
        }
    })
   
</script>

<style>
.tareaRealizada {
    text-decoration: line-through;
}
</style>
