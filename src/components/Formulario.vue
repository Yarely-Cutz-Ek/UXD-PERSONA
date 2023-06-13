<script>
import btn from '../components/submit.vue';
import text1 from '../components/texto.vue';
import slider from '../components/sli.vue';
import tarea from '../components/methods.vue';

import axios from "axios";
let API_URL = `/api/guardarPersonasUxd.php`;
export default {
  components: {

    btn, text1, slider, tarea
  },
  emits: ['person', 'info', 'dato', 'datoTexto'],

  data() {
    return {
      nombre: "",
      edad: "",
      estadoCivil: "",
      trabajo: "",
      residencia: "",
      cita: "",  
      citaAutor: "",
      bio: "",
      personalidad01: 50,
      personalidad02: 50,
      personalidad03: 50,
      personalidad04: 50,
      objetivos: "",//[ {value: ''} ],
      frustraciones:"" ,//[{value: 'obj20'}],
      motivaciones: "",//[{value: 'motivacion','porcentaje':'80'}],
      porcentaje: "",
      marcas: "",
      Mostrar1: true,
      Mostrar2: false,
      Mostrar3: false,
    };
  },
  mounted() {
        

      },
  methods: {
      bio1(y){
                this.bio=y;

            },
      cita1(t){
                this.cita=t;

            },
      citaAutor1(t){
                this.citaAutor=t;

            },
      nombre1(a){
                this.nombre=a;

            },
      edad1(a){
                this.edad=a;

            },
      trabajo1(a){
                this.trabajo =a;

            },

      resi1(a){
                this.residencia =a;

            },
      
      
      pers1(s){
                this.personalidad1=s;

            }
      ,
      pers2(s){
                this.personalidad2=s;

            }
      ,
      pers3(s){
                this.personalidad3=s;

            }
      ,
      pers4(s){
                this.personalidad4=s;

            }
      ,
      obj1(a){
                this.objetivos=a;

            }
      ,
      frust1(a){
                this.frustraciones=a;

            }
      ,
      moti1(a){
                this.motivaciones=a;

            }
      ,
      marca1(a){
                this.marcas=a;

            },
    summit() {
      API_URL + this.pagina;
      console.log(API_URL);
      axios.post("/api/guardarPersonasUxd.php", {
        nombre: this.nombre,
        edad: this.edad,
        estadoCivil: this.estadoCivil,
        trabajo: this.trabajo,
        residencia: this.residencia,
        cita: this.cita,
        citaAutor: this.citaAutor,
        bio: this.bio,
        personalidad01: this.personalidad01,
        personalidad02: this.personalidad02,
        personalidad03: this.personalidad03,
        personalidad04: this.personalidad04,
        objetivos: this.objetivos,
        frustraciones: this.frustraciones,
        motivaciones: this.motivaciones,
        porcentaje: this.porcentaje,
        marcas: this.marcas,
        //completar las variables, estas deben llamarse como las que se recibirán en el backend sin el símbolo del dolar $
      })
        .then((response) => {
          console.log(response.status)
        });

    },


    validar() {
      //nombre
      if (this.Nombre != "" && !isNaN(this.nombre) === false && this.nombre.length < 201 && this.nombre.length > 2) {
        console.log("el nombre es correcto")

        //edad
        if (this.edad.length < 3 && this.edad != "") {
          console.log("edad existe")
        } else {
          console.log("no existe esa edad")
        }

        //Estado civil
        if (this.estadoCivil != "") {
          console.log("si selecciono estado civil")
        } else {
          console.log("no selecciono estado civil")
          return false
        }

        //Trabajo
        if (this.trabajo.length < 201 && this.trabajo != "" && !isNaN(this.trabajo) === false) {
          console.log("trabajo existe")
        } else {
          console.log("no existe trabajo")
          return false
        }

        //Residencia
        if (this.residencia.length < 201 && this.residencia != "" && !isNaN(this.residencia) === false) {
          console.log("residencia existe")
        } else {
          console.log("no existe residencia")
          return false
        }

        //Cita
        if (this.cita.length < 501 && this.cita != "" && !isNaN(this.cita) === false) {
          console.log("Cita existe")
        } else {
          console.log("Cita no existe")
          return false
        }

        //CitaAutor
        if (this.citaAutor.length < 501 && this.citaAutor != "" && !isNaN(this.citaAutor) === false) {
          console.log("CitaAutor existe")
        } else {
          console.log("CitaAutor no existe")
          return false
        }

        //Bio
        if (this.bio.length < 701 && this.bio != "" && !isNaN(this.bio) === false) {
          console.log("Bio correcta")
        } else {
          console.log("Bio incorrecta")
          return false
        }

        return true

      }
      else {
        console.log("No pude registrarlo")
        return false
      }


    },
    ocultar1() {
      return this.Mostrar1 = true, this.Mostrar2 = false, this.Mostrar3 = false
    },

    ocultar2() {
      return this.Mostrar1 = false, this.Mostrar2 = true, this.Mostrar3 = false
    },

    ocultar3() {
      return this.Mostrar1 = false, this.Mostrar2 = false, this.Mostrar3 = true
    },
  },

};

</script>
<template>
  <section class="bg-gray-100">
    <div class="grid grid-cols-3">
      <div></div>
      <div class="mx-auto max-w-screen-xl px-4 py-16 sm:px-6 lg:px-8">
        <div>


          <div class="rounded-lg bg-white p-8 shadow-lg lg:col-span-3 lg:p-12">
            <form v-on:submit.prevent action="" class="space-y-4">


              <div id="Formulario 1" v-show:value="Mostrar1">
                <div>
                  <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="nombre">
                    Nombre
                  </label>
                  <text1 @info= " nombre1 " > Yarely</text1>


                </div>

                <div class="grid grid-cols-1 gap-4 sm:grid-cols-2">
                  <div>
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="edad">
                      Edad
                    </label>
                    <text1 @info= " edad1 " > 22</text1>

                  </div>

                  <div>
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="estadoCivil">
                      ESTADO CIVIL
                    </label>
                    <div class="relative">
                      <select v-model="estadoCivil" class="w-full rounded-lg border-gray-200 p-3 text-sm"
                        id="estadoCivil">
                        <option value="1">Soltero</option>
                        <option value="2">Casado</option>
                        <option value="3">Divorciado</option>
                        <option value="4">Separado</option>
                        <option value="5">Unión libre</option>
                        <option value="6">Viudo</option>
                      </select>
                    </div>
                  </div>
                </div>

                <div class="grid grid-cols-1 gap-4 sm:grid-cols-2">
                  <div>
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="trabajo">
                      TRABAJO
                    </label>
                    <text1 @info= " trabajo1 " > Estudiante</text1>
                  </div>

                  <div>
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="residencia">
                      Residencia
                    </label>
                    <text1 @info= " resi1 " > Motul</text1>
                  </div>
                </div>

                <div class="grid grid-cols-1 gap-4 sm:grid-cols-2">
                  <div>
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="cita">
                      CITA
                    </label>
                    <text1 @info= " cita1 " > </text1>
                  </div>

                  <div>
                    <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="citaAutor">
                      CITA AUTOR
                    </label>
                    <text1 @info= " citaAutor1" > </text1>
                  </div>
                </div>

                <div>
                  <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="bio">
                    BIO
                  </label>
                  <tarea @info= " bio1 " > </tarea>

                </div>


                <button class="inline-block w-full rounded-lg bg-black px-5 py-3 font-medium text-white sm:w-auto"
                  @click="ocultar2()">siguiente</button>
              </div>

              <div id="Formulario 2" v-show:value="Mostrar2">
                <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                  Personalidad 1.- Mente
                </label><br>
                  <slider @person="pers1"></slider>


                <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                  Personalidad 2.- Energía
                </label><br>
                <slider @person="pers2"></slider>
                

                <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                  Personalidad 3.-Naturaleza
                </label><br>

                <slider @person="pers3"></slider>

                <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                  Personalidad 4.- Identidad
                </label><br>
                <slider @person="pers4"></slider>
                <div class="grid grid-cols-3">


                  <div class="p-6">
                    <button
                      class=" p-3 0inline-block w-full rounded-lg bg-black px-5 py-3 font-medium text-white sm:w-auto"
                      @click="ocultar1()">Anterior</button>
                  </div>
                  <div></div>


                  <div class="p-6">
                    <button
                      class=" p-3 inline-block w-full rounded-lg bg-black px-5 py-3 font-medium text-white sm:w-auto"
                      @click="ocultar3()">Siguiente</button>
                  </div>
                </div>


              </div>

              <div id="Formulario 3" v-show:value="Mostrar3">

                <div class="py-2">
                  <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="objetivos">
                    OBJETIVOS
                  </label>
                  <text1 @info= "obj1" > </text1>

                </div>


                <div class="py-2">
                  <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="frustraciones">
                    FRUSTRACIONES
                  </label>
                  <text1 @info= "frust1" > </text1>

                </div>

                <div class="py-2">
                  <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="motivaciones">
                    MOTIVACIONES
                  </label>
                  <text1 @info= "moti1" > </text1>

                </div>


                <div class="py-2">
                  <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="marcas">
                    MARCAS
                  </label>
                  <text1 @info= "marca1" > </text1>

                </div>
                <div class="grid grid-cols-3">


                  <div class="p-6">
                    <button class="0inline-block w-full rounded-lg bg-black px-5 py-3 font-medium text-white sm:w-auto"
                      @click="ocultar2()">Anterior</button>
                  </div>
                  <div></div>



                  <div class="p-6">
                    <button type="submit" @click="summit()"
                      class="inline-block w-full rounded-lg bg-black px-5 py-3 font-medium text-white sm:w-auto">
                      Registrar
                    </button>
                  </div>
                </div>

              </div>
            </form>
          </div>
        </div>
      </div>
      <div></div>
    </div>
  </section>
</template>
<script>

</script>