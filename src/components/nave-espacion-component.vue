<template>
  <div class="container mt-3" >
    <h1>{{ msg }}</h1>
    <br><br>

    <div class="row">
      <div class="col-sm-4">
        <div class="card" style="width: 18rem;">
        <img src="../assets/Vehiculo-lanzadera.jpg" class="card-img-top" alt="img..." width="50" height="320">
          <div class="card-body">
            <h5 class="card-title">Vehiculo Lanzadera</h5>
            <p class="card-text">Nave tripulada con capacidad de tales y pacuales</p>
            <a @click="cambiarEstadoLanzadera()" class="btn btn-primary">Ver..</a>
            <br><br>
            <a @click="crearLanzadera()" class="btn btn-primary">Crear</a>
          </div>
        </div>
      </div>
       
      <div class="col-sm-4">
        <div class="card" style="width: 18rem;">
        <img src="../assets/nvae-tripulada.jpg" class="card-img-top" alt="img..." width="50" height="320">
          <div class="card-body">
            <h5 class="card-title">Nave Espacial No tripulada</h5>
            <p class="card-text">Nave tripulada con capacidad de tales y pacuales</p>
            <a class="btn btn-primary" @click="cambiarEstadoNoTripulada()">Ver..</a>
            <br><br>
            <a @click="crearNoTripulada()" class="btn btn-primary">Crear</a>
          </div>
        </div>
      </div>

      <div class="col-sm-4">
        <div class="card" style="width: 18rem;">
        <img src="../assets/Vehiculo-lanzadera.jpg" class="card-img-top" alt="img..." width="50" height="320">
          <div class="card-body">
            <h5 class="card-title">Nave Espacial tripulada</h5>
            <p class="card-text">Nave tripulada con capacidad de tales y pacuales</p>
            <a class="btn btn-primary" @click="cambiarEstadoTripulada()">Ver..</a>
            <br><br>
            <a @click="crearTripulada()" class="btn btn-primary">Crear</a>
          </div>
        </div>     
      </div>
  </div>
    
    <br>
    <br>
    <div v-if="crearVehiculoLanzadera">
      <h4>Vehiculo Lanzadera</h4>
        <input type="text" class="form-control my-3" name="nombrenave" id="nombrenave" placeholder="Ingrese nombre nave" v-model="nombreNave" title="Escribe el nombre de la nave">              
        <input type="text" class="form-control my-3" v-model="paisNave" placeholder="Ingrese país nave" title="Escribe el pais de la nave">
        <input type="date" class="form-control my-3" v-model="actividadNave" placeholder="Actividad nave" title="Escribe el inicio de la actividad">
        <input type="number" class="form-control my-3" v-model="velocidadNave" placeholder="Ingrese velocidad de la nave" title="Escribe la velocidad de la nave">
        <input type="text" class="form-control my-3" v-model="combustibleNave" placeholder="Ingrese combusible de la nave" title="Escribe el tipo de combustible">
        <input type="number" class="form-control my-3" v-model="pesoNave" placeholder="Ingrese peso de la nave" title="Escribe el peso">
        <input type="number" class="form-control my-3" v-model="altoNave" placeholder="Ingrese alto de la nave" title="Escribe el alto">
        <!--<input type="text" class="form-control my-3" v-model="tipoNave" placeholder="Ingrese tipo de la nave" title="Escribe el tipo de nave">-->
        <div class="form-control my-3">
            <select v-model="tipoNaves" class="form-control" id="tipoNave">
                <option disabled value="">Seleccione tipo nave</option>
                <option :value="tipoNaves[0]">{{tipoNaves[0]}}</option>
                <option :value="tipoNaves[1]">{{tipoNaves[1]}}</option>
                <option :value="tipoNaves[2]">{{tipoNaves[2]}}</option>
            </select>
      </div>

        <input type="number" class="form-control my-3" v-model="capacidadNave" placeholder="Ingrese la capacidad de toneladas" title="Escribe la capacidad de carga">
        <input type="number" class="form-control my-3" v-model="potenciaNave" placeholder="Ingrese la potencia nave"  title="Escribe la potencia de la nave">
        <input type="text" class="form-control my-3" v-model="sistemaPropulsionNave" placeholder="Ingrese el sistema de propulsion"  title="Escribe el sistema de propulsión">
        <input type="text" class="form-control my-3" v-model="tipoCargaNave" placeholder="Carga" title="Escribe el tipo de carga">    
        <button class="btn btn-primary" @click.prevent="enviarDatos()">Agregar</button>
    </div>
    <div v-if="vehiculoLanzadera">                       
      <br>
      <br>
      <h3>Lista vehiculos lanzadera</h3>
      <input type="text" class="form-control my-3" v-model="busquedaNaveLanzadera" placeholder="Buscar.."  title="Buscar...">
      <button class="btn btn-primary" @click.prevent="btnbusquedaNaveLanzadera()">Buscar</button>
      <table class="table">
            <thead>
                <tr>
                    <th scope="col">Nombre</th>
                    <th scope="col">Pais</th>
                    <th scope="col">Actividad</th>
                    <th scope="col">Velocidad</th>
                    <th scope="col">Combustible</th>
                    <th scope="col">Peso</th>
                    <th scope="col">Alto</th>
                    <th scope="col">Tipo</th>
                    <th scope="col">Capacidad</th>
                    <th scope="col">Potencia</th>
                    <th scope="col">Sistema Propulsion</th>
                    <th scope="col">Tipo Carga</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="nave in naveLanzadera" :key="nave.id">
                    <td>{{nave.nombre}}</td>
                    <td>{{nave.pais}}</td>
                    <td>{{nave.actividad}}</td>
                    <td>{{nave.velocidad}}</td>
                    <td>{{nave.tipoCombustible}}</td>
                    <td>{{nave.peso}}</td>
                    <td>{{nave.alto}}</td>
                    <td>{{nave.tipo}}</td>
                    <td>{{nave.capacidadCarga}}</td>
                    <td>{{nave.potencia}}</td>
                    <td>{{nave.sistemaPropulsion}}</td>
                    <td>{{nave.tipoCarga}}</td>
                </tr>
            </tbody>
      </table>   
    </div>

    <div v-if="crearVehiculoNoTripulado">
      <h4>Nave Espacial No tripulada</h4>
      <input type="text" class="form-control my-3" placeholder="Ingrese nombre nave" v-model="nombreNave" title="Escribe el nombre de la nave">
      <input type="text" class="form-control my-3" placeholder="Ingrese país nave" v-model="paisNave" title="Escribe el pais de la nave">
      <input type="date" class="form-control my-3" placeholder="Actividad nave" v-model="actividadNave" title="Escribe el inicio de la actividad">
      <input type="number" class="form-control my-3" placeholder="Ingrese velocidad de la nave" v-model="velocidadNave" title="Escribe la velocidad de la nave">
      <input type="text" class="form-control my-3" v-model="combustibleNave" placeholder="Ingrese combusible de la nave" title="Escribe el tipo de combustible">
      <input type="number" class="form-control my-3" v-model="pesoNave" placeholder="Ingrese peso de la nave" title="Escribe el peso">
      <input type="number" class="form-control my-3" v-model="altoNave" placeholder="Ingrese alto de la nave" title="Escribe el alto">
     <!-- <input type="text" class="form-control my-3" v-model="tipoNave" placeholder="Ingrese tipo de la nave" title="Escribe el tipo de nave">-->
      <div class="form-control my-3">
            <select v-model="tipoNaves" class="form-control" id="tipoNave">
                <option disabled value="">Seleccione tipo nave</option>
                <option :value="tipoNaves[0]">{{tipoNaves[0]}}</option>
                <option :value="tipoNaves[1]">{{tipoNaves[1]}}</option>
                <option :value="tipoNaves[2]">{{tipoNaves[2]}}</option>
            </select>
      </div>
      <input type="number" class="form-control my-3" v-model="catidadMotores"  placeholder="Ingrese cantidad motores  de la nave" title="Escribe la cantidad de motores">
      <input type="text" class="form-control my-3" v-model="tipoEstudio" placeholder="Ingrese tipo de estudio" title="Escribe el tipo de estudio">
      
      <button class="btn btn-primary" @click.prevent="enviarDatosNoTripulada()">Agregar</button>
    </div>
    <div v-if="vehiculoNoTripulado">
      <br>
      <br>
      <h3>Lista naves Espaciales No Tripuladas</h3>
       <input type="text" class="form-control my-3" v-model="busquedaNaveNoTripulada" placeholder="Buscar.."  title="Buscar...">
      <button class="btn btn-primary" @click.prevent="btnbusquedaNaveNoTripulada()">Buscar</button>
    
      <table class="table">
            <thead>
                <tr>
                    <th scope="col">Nombre</th>
                    <th scope="col">Pais</th>
                    <th scope="col">Actividad</th>
                    <th scope="col">Velocidad</th>
                    <th scope="col">Combustible</th>
                    <th scope="col">Peso</th>
                    <th scope="col">Alto</th>
                    <th scope="col">Tipo</th>
                    <th scope="col">Cantidad motores</th>
                    <th scope="col">Tipo Estudio</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="nave in navesNotripuladas" :key="nave.id">
                    <td>{{nave.nombre}}</td>
                    <td>{{nave.pais}}</td>
                    <td>{{nave.actividad}}</td>
                    <td>{{nave.velocidad}}</td>
                    <td>{{nave.tipoCombustible}}</td>
                    <td>{{nave.peso}}</td>
                    <td>{{nave.alto}}</td>
                    <td>{{nave.tipo}}</td>
                    <td>{{nave.cantidadMotores}}</td>
                    <td>{{nave.tipoEstudio}}</td>

                </tr>
            </tbody>
      </table>
    </div>

    <div v-if="crearVehiculoTripulado">
      <h4>Nave Espacial tripulada</h4>
      <input type="text" class="form-control my-3" placeholder="Ingrese nombre nave" v-model="nombreNave" title="Escribe el nombre de la nave">
      <input type="text" class="form-control my-3" placeholder="Ingrese país nave" v-model="paisNave" title="Escribe el pais de la nave">
      <input type="date" class="form-control my-3" placeholder="Actividad nave" v-model="actividadNave" title="Escribe el inicio de la actividad">
      <input type="number" class="form-control my-3" placeholder="Ingrese velocidad de la nave" v-model="velocidadNave" title="Escribe la velocidad de la nave">
      <input type="text" class="form-control my-3" v-model="combustibleNave" placeholder="Ingrese combusible de la nave" title="Escribe el tipo de combustible">
      <input type="number" class="form-control my-3" v-model="pesoNave" placeholder="Ingrese peso de la nave" title="Escribe el peso">
      <input type="number" class="form-control my-3" v-model="altoNave" placeholder="Ingrese alto de la nave" title="Escribe el alto">
     <!-- <input type="text" class="form-control my-3" v-model="tipoNave" placeholder="Ingrese tipo de la nave" title="Escribe el tipo de nave">-->
      <div class="form-control my-3">
            <select v-model="tipoNaves" class="form-control" id="tipoNave">
                <option disabled value="">Seleccione tipo de nave</option>
                <option :value="tipoNaves[0]">{{tipoNaves[0]}}</option>
                <option :value="tipoNaves[1]">{{tipoNaves[1]}}</option>
                <option :value="tipoNaves[2]">{{tipoNaves[2]}}</option>
            </select>
      </div>

      <input type="number" class="form-control my-3" v-model="cantidadPersonas" placeholder="Ingrese capacidad de personas" title="Escribe la cantidad de personas">
      <!--<input type="text" class="form-control my-3" v-model="tipoObjetivo" placeholder="Ingrese el objetivo de estudio" title="Escribe el tipo objetivo">      -->

      <div class="form-control my-3">
            <select v-model="tipoObjetivo" class="form-control" id="tipoObjetivo">
                <option disabled value="">Seleccione objeto estudio</option>
                <option :value="tipoEstudios[0]">{{tipoEstudios[0]}}</option>
                <option :value="tipoEstudios[1]">{{tipoEstudios[1]}}</option>
                <option :value="tipoEstudios[2]">{{tipoEstudios[2]}}</option>
            </select>
      </div>
  
      <button class="btn btn-primary" @click.prevent="enviarDatosTripulada()">Agregar</button>
    </div>

    <div v-if="vehiculoTripulado">      
      <br>
      <br>
      <h3>Lista naves Espaciales Tripuladas</h3>
      <input type="text" class="form-control my-3" v-model="busquedaNaveTripulada" placeholder="Buscar.."  title="Buscar...">
      <button class="btn btn-primary" @click.prevent="btnbusquedaNaveTripulada()">Buscar</button>
     
      <table class="table">
            <thead>
                <tr>
                  <th scope="col">Nombre</th>
                  <th scope="col">Pais</th>
                  <th scope="col">Actividad</th>
                  <th scope="col">Velocidad</th>
                  <th scope="col">Combustible</th>
                  <th scope="col">Peso</th>
                  <th scope="col">Alto</th>
                  <th scope="col">Tipo</th>
                  <th scope="col">Cantidad Personas</th>
                  <th scope="col">Estudio Objetivo</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="nave in navestripuladas" :key="nave.id">
                    <td>{{nave.nombre}}</td>
                    <td>{{nave.pais}}</td>
                    <td>{{nave.actividad}}</td>
                    <td>{{nave.velocidad}}</td>
                    <td>{{nave.tipoCombustible}}</td>
                    <td>{{nave.peso}}</td>
                    <td>{{nave.alto}}</td>
                    <td>{{nave.tipo}}</td>
                    <td>{{nave.cantidadPersonas}}</td>
                    <td>{{nave.tipoObjetivo}}</td>
                    
                    
                </tr>
            </tbody>
      </table>
    </div>
    
  </div>
</template>

<script>
const axios = require('axios');
export default {
  /**
   * Declarar variables
   */
  data: function() {
     return {
      name: "HelloWorld",
      nombreNave: "",
      paisNave: "",
      actividadNave: "",
      velocidadNave : "",
      combustibleNave: "",
      pesoNave: "",
      altoNave: "",
      tipoNave: "",
      capacidadNave: "",
      potenciaNave: "",
      sistemaPropulsionNave: "",
      tipoCargaNave: "",
      catidadMotores:"",
      tipoEstudio:"",
      cantidadPersonas: "",
      tipoObjetivo:"",

      busquedaNaveLanzadera: "",
      busquedaNaveNoTripulada : "",
      busquedaNaveTripulada: "",
      crearVehiculoLanzadera:false,
      vehiculoLanzadera :false,
      crearVehiculoTripulado: false,
      vehiculoTripulado:false,
      crearVehiculoNoTripulado:false,
      vehiculoNoTripulado:false,

      navestripuladas: [],
      naveLanzadera:[],
      navesNotripuladas:[],
      tipoEstudios:["MISIONLUNAR","COMPORTAMIENTOHUMANO","MANTENIMIENTOSATELITES"],
      tipoNaves:["Vehiculo Lanzadera","Nave Espacial Tripulada","Nave Espacial No Tripulada"],
     };
  },
  methods: {

    /**
     * Hace el llamado de la lista de vehiculo lanzadera
     */
    listarDatos() {
      axios.get("https://navesespacialesestacion-production.up.railway.app/naves/listarVehiculoLanzadera")
            .then(response => {
                console.log(response.data);   
                this.naveLanzadera =  response.data ;
            })
            .catch(error => {    
              console.log(error)            
                });
    },

    /**
     * Hace el llamado de la lista de vehiculos nave tripulada
     */
    listarDatosTripulada() {
      axios.get("https://navesespacialesestacion-production.up.railway.app/naves/listarNaveTripulada")
            .then(response => {
                console.log(response.data);   
                this.navestripuladas =  response.data ;
            })
            .catch(error => {    
              console.log(error)            
                });
    },   
    /**
     * Hace el llamado de la lista de vehiculo naves no tripulada
     */ 
    listarDatosNoTripulada() {
      axios.get("https://navesespacialesestacion-production.up.railway.app/naves/listarNaveNoTripulada")
            .then(response => {
                console.log(response.data);   
                this.navesNotripuladas =  response.data ;
            })
            .catch(error => {    
              console.log(error)            
                });
    },

    /**
     * Busca registros de nave lanzadera por coincidencia en el nombre
     */
    btnbusquedaNaveLanzadera(){
      var nombre = this.busquedaNaveLanzadera;
        axios.get(`https://navesespacialesestacion-production.up.railway.app/naves/buscarVehiculoLanzadera/${nombre}`)
            .then(response => {
                this.naveLanzadera =  response.data ;
            })
            .catch(error => {    
              console.log(error)            
            });
    },

    /**
     * Busca registros de nave no tripulada por coincidencia en el nombre
     */
    btnbusquedaNaveNoTripulada(){
      var nombre = this.busquedaNaveNoTripulada;
        axios.get(`https://navesespacialesestacion-production.up.railway.app/naves/buscarNaveNoTripulada/${nombre}`)
        //axios.get(`http://localhost:8081/naves/buscarNaveNoTripulada/${nombre}`)
            .then(response => {
                this.navesNotripuladas =  response.data ;
            })
            .catch(error => {    
              console.log(error)            
            });
    },

    /**
     * Busca registros de nave no tripulada por coincidencia en el nombre
     */
    btnbusquedaNaveTripulada(){
      var nombre = this.busquedaNaveTripulada;
        axios.get(`https://navesespacialesestacion-production.up.railway.app/naves/buscarNaveTripulada/${nombre}`)
        //axios.get(`http://localhost:8081/naves/buscarNaveTripulada/${nombre}`)
            .then(response => {
                this.navestripuladas =  response.data ;
            })
            .catch(error => {    
              console.log(error)            
            });
    },

     /**
     * Guarda registro de vehiculo lanzadera
     */
     enviarDatos() {
      const parametrosNave = {
                nombre: this.nombreNave,                   
                pais: this.paisNave,
                actividad: this.actividadNave,
                velocidad: this.velocidadNave,
                tipoCombustible: this.combustibleNave,
                peso: this.pesoNave,
                alto: this.altoNave,
                tipo: this.tipoNave,
                capacidadCarga: this.capacidadNave,
                potencia: this.potenciaNave,
                sistemaPropulsion: this.sistemaPropulsionNave,
                tipoCarga: this.tipoCargaNave,
      };
      console.log(parametrosNave)
      axios.post("https://navesespacialesestacion-production.up.railway.app/naves/guardarVehiculoLanzadera", parametrosNave)
            .then(response => {
                console.log(response.data);
                this.listarDatos();
                this.nombreNave = "",                   
                this.paisNave="",
                this.actividadNave="",
                this.velocidadNave="",
                this.combustibleNave="",
                this.pesoNave="",
                this.altoNave="",
                this.tipoNave="",
                this.capacidadNave="",
                this.potenciaNave="",
                this.sistemaPropulsionNave="",
                this.tipoCargaNave=""
            })
            .catch(error => {    
              console.log(error)            
                });
    },

    /**
     * Guarda registro de nave no tripulada
     */
     enviarDatosNoTripulada() {
      const parametrosNave = {
                nombre: this.nombreNave,                   
                pais: this.paisNave,
                actividad: this.actividadNave,
                velocidad: this.velocidadNave,
                tipoCombustible: this.combustibleNave,
                peso: this.pesoNave,
                alto: this.altoNave,
                tipo: this.tipoNave,
                cantidadMotores:this.catidadMotores,
                tipoEstudio:this.tipoEstudio,
                
      };
      console.log(parametrosNave)
      axios.post("https://navesespacialesestacion-production.up.railway.app/naves/guardarNaveNoTripulada", parametrosNave)
            .then(response => {
                console.log(response.data);
                this.listarDatosNoTripulada();
                this.nombreNave = "",                   
                this.paisNave="",
                this.actividadNave="",
                this.velocidadNave="",
                this.combustibleNave="",
                this.pesoNave="",
                this.altoNave="",
                this.tipoNave="",
                this.catidadMotores="",
                this.tipoEstudio=""
            })
            .catch(error => {    
              console.log(error)            
                });
    },

    /**
     * Guardar registro de nave tripulada
     */
    enviarDatosTripulada() {
      const parametrosNave = {
                nombre: this.nombreNave,                   
                pais: this.paisNave,
                actividad: this.actividadNave,
                velocidad: this.velocidadNave,
                tipoCombustible: this.combustibleNave,
                peso: this.pesoNave,
                alto: this.altoNave,
                tipo: this.tipoNave,
                cantidadPersonas: this.cantidadPersonas,
                tipoObjetivo: this.tipoObjetivo
      };
      axios.post("https://navesespacialesestacion-production.up.railway.app/naves/guardarNaveTripulada", parametrosNave)
            .then(response => {
                console.log(response.data);
                this.listarDatosTripulada();
                this.nombreNave = "",                   
                this.paisNave="",
                this.actividadNave="",
                this.velocidadNave="",
                this.combustibleNave="",
                this.pesoNave="",
                this.altoNave="",
                this.tipoNave="",
                this.cantidadPersonas="",
                this.tipoObjetivo=""
            })
            .catch(error => {    
              console.log(error)            
                });
    },

    

    /**
     * Metodos de validacion 
     */
    crearLanzadera(){
      this.crearVehiculoLanzadera=true,
      this.crearVehiculoTripulado= false,
      this.crearVehiculoNoTripulado=false,
      this.vehiculoLanzadera = false;      
      this.vehiculoTripulado=false,
      this.vehiculoNoTripulado=false
    },
    cambiarEstadoLanzadera(){
      this.listarDatos();
      this.vehiculoLanzadera = true;      
      this.vehiculoTripulado=false,
      this.vehiculoNoTripulado=false,
      this.crearVehiculoLanzadera=false,
      this.crearVehiculoTripulado= false,
      this.crearVehiculoNoTripulado=false  
    },
    crearNoTripulada(){
      this.crearVehiculoLanzadera=false,
      this.crearVehiculoTripulado= false,
      this.crearVehiculoNoTripulado=true,
      this.vehiculoLanzadera = false;      
      this.vehiculoTripulado=false,
      this.vehiculoNoTripulado=false
    },
    cambiarEstadoNoTripulada(){
      this.listarDatosNoTripulada();
      this.vehiculoLanzadera = false;      
      this.vehiculoTripulado=false,
      this.vehiculoNoTripulado=true,
      this.crearVehiculoLanzadera=false,
      this.crearVehiculoTripulado= false,
      this.crearVehiculoNoTripulado=false      
    },
    crearTripulada(){
      this.crearVehiculoLanzadera=false,
      this.crearVehiculoTripulado= true,
      this.crearVehiculoNoTripulado=false,
      this.vehiculoLanzadera = false;      
      this.vehiculoTripulado=false,
      this.vehiculoNoTripulado=false
    },
    cambiarEstadoTripulada(){
      this.listarDatosTripulada();
      this.vehiculoLanzadera = false;      
      this.vehiculoTripulado=true,
      this.vehiculoNoTripulado=false, 
      this.crearVehiculoLanzadera=false,
      this.crearVehiculoTripulado= false,
      this.crearVehiculoNoTripulado=false     
    } 
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
